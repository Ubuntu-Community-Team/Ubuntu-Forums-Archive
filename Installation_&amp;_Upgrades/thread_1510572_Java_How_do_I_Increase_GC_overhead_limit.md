---
title: "Java: How do I Increase GC overhead limit"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by g000we on 2010-06-15
Dear Ubuntu Gurus,

I've run a script which I need to parse a lot of data through to a webapp.

I got this error with my ruby script, running through jruby, firing into an apache webapp:

Java/util/Array.java:#### java.lang.OutOfMemoryError: GC overhead limit exceeded (NativeException)

(Where #### was the line number)

I've looked at:

[http://java.sun.com/javase/technologies/hotspot/gc/gc_tuning_6.html#par_gc.oom](http://java.sun.com/javase/technologies/hotspot/gc/gc_tuning_6.html#par_gc.oom)

I think it suggests I do: 

[IMG]http://java.sun.com/im/a.gif[/IMG]  ```

-XX:+UseConcMarkSweepGC -XX:+CMSIncrementalMode \

-XX:+PrintGCDetails -XX:+PrintGCTimeStamps \

-XX:+CMSIncrementalPacing -XX:CMSIncrementalDutyCycleMin=0

-XX:CMSIncrementalDutyCycle=10

``` 

My java version:
```


java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK 64-Bit Server VM (build 14.0-b16, mixed mode)


```

Q1: How do I implement that into the java/util/Arrays.java file?
Q2: Is there a way of temporary making the Java VM/JDK have better handled GC overhead?

Q3: Is this the right area/forum for this post?

Any guidance would be much appreciated.

Regards,

g000we

---

### Post by kbielefe on 2010-06-15
For how to pass java command line options, you'd probably have better luck posting to the [jruby user list]("http://xircles.codehaus.org/lists/user@jruby.codehaus.org").

However, most likely your script needs to be changed rather than the GC handling.  Try to rewrite it without so many objects being created and deleted.  Can't really be more specific than that since I haven't seen your script and don't know much Ruby anyway.
[]("http://xircles.codehaus.org/lists/user@jruby.codehaus.org")

---

