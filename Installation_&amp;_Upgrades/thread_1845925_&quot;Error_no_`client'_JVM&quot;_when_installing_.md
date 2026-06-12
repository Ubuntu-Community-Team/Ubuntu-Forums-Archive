---
title: "&quot;Error: no `client' JVM&quot; when installing and uninstalling"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by Juvr on 2011-09-18
Hi all!

I'm fairly experienced with Ubuntu and other Linux distros, but for the first time ever I've run into a problem that I couldn't find a solution for.
A couple of days ago I upgraded from 11.04 32-bit to 11.04 64-bit and now I'm in the process of reinstalling all the software and configure everything to my liking.
When I installed the ubuntu-restricted-extras I got an error message saying
 
"Error: no `client' JVM at `/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/client/libjvm.so'."

and then 

"Error adding brasil.gov.br/brasil.gov.br.crt
Error adding cacert.org/cacert.org.crt"

and so on another fifty times or so with different files and after that it ends with 

"failed (VM used: java-6-openjdk).
dpkg: error processing ca-certificates-java (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ca-certificates-java
E: Sub-process /usr/bin/dpkg returned an error code (1)"

Now every time I install or uninstall something I get the same error.
Things are still being installed and seems to work just fine and ubuntu-restricted-extras seems to be doing what it should.

Any ideas what could be causing this?

---

