# deps-flamegraph

Converts the transitive dependencies of a java gradle project into a flame
graph. Allows to see the cumulated and relative size of all dependencies.

The `stackcollapse-gradle-dependencies.pl` script takes the output of 
`gradle dependencies` and converts it to a format accepted by flamegraph.pl

## Usage
```
USAGE: stackcollapse-gradle-dependencies.pl [options] infile > outfile

  --org             # include dependency organisation
  --version         # include dependency version
  --no-size         # ignore jar size
  --jar-cache DIR   # specify alternate path for gradle jar cache

```

Otherwise, you can use the `deps-flamegraph` bash script to directly 
generate the SVG file.

## Example

See included [example](https://github.com/pcdv/deps-flamegraph/tree/master/samples/cassandra) 
that computes the dependencies of Cassandra.

![alt text](samples/cassandra/deps-runtime.svg "Cassandra dependencies")

The file was generated by running `../../deps-flamegraph` under `samples/cassandra`.
```
$ ../../deps-flamegraph
Could not find flamegraph.pl, getting it from GitHub
Cloning into 'FlameGraph'...
remote: Counting objects: 949, done.
remote: Total 949 (delta 0), reused 0 (delta 0), pack-reused 949
Receiving objects: 100% (949/949), 1.82 MiB | 832.00 KiB/s, done.
Resolving deltas: 100% (541/541), done.
Computing cassandra runtime dependencies. Set CONFIGURATION=test (or other) to use another configuration
Generated deps-runtime.svg
```

NB: the SVG is interactive but this does not work in GitHub (clone the project to see for yourself).



