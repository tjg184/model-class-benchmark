# Benchmarking JVM model classes

This is a quick study of the relative performance of the typical DTO methods generated by Groovy 2.4.3 annotations, Scala 2.11.6 case classes, Kotlin 0.11.91.1 data classes, and Lombok, all running on Oracle Java 8u40.  These tests use the Groovy indy jar and compile flag.  The Groovy model object is decorated with `@CompileStatic`.

I'm impatient, so each benchmark is running with 20 warmups, 50 iterations, and 1 fork.  The benchmark is sampling for average time in nanoseconds.

## equals()

    Benchmark                         Mode  Cnt     Score    Error  Units
    EqualsBenchmark.equalsGroovy      avgt   50    57.035 ±   2.883  ns/op
    EqualsBenchmark.equalsKotlin      avgt   50    80.416 ±   3.494  ns/op
    EqualsBenchmark.equalsLombok      avgt   50    26.124 ±   1.156  ns/op
    EqualsBenchmark.equalsScala       avgt   50    51.966 ±   2.416  ns/op

## hashCode()

    Benchmark                         Mode  Cnt     Score    Error  Units
    HashCodeBenchmark.hashCodeGroovy  avgt   50  1337.638 ±  60.966  ns/op
    HashCodeBenchmark.hashCodeKotlin  avgt   50    63.097 ±   3.222  ns/op
    HashCodeBenchmark.hashCodeLombok  avgt   50    61.493 ±   2.885  ns/op
    HashCodeBenchmark.hashCodeScala   avgt   50   139.673 ±   6.056  ns/op
    
## toString()

    Benchmark                         Mode  Cnt     Score     Error  Units
    ToStringBenchmark.toStringGroovy  avgt   50  2990.375 ± 148.777  ns/op
    ToStringBenchmark.toStringKotlin  avgt   50   463.005 ±  16.999  ns/op
    ToStringBenchmark.toStringLombok  avgt   50   440.080 ±  18.320  ns/op
    ToStringBenchmark.toStringScala   avgt   50   753.451 ±  31.255  ns/op
