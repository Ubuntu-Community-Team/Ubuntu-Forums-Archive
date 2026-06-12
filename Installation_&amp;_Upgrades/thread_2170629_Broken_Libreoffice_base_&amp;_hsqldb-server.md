---
title: "Broken Libreoffice base &amp; hsqldb-server"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by beaucoder2 on 2013-08-27
Hi All,

Ubuntu 13.04 32bit pae. 

Decided to install (add) Libreoffice Base. Error message creating DB connection on first attempt: libhsqldb-java missing. Installed same via USC. 

Created a small test DB. Worked OK the first time. Table with 5 fields and 5 records. 

Second attempt to edit file caused "out of memory" error. 

Tried to install hsqldb-server to see if that would help. Would not install. Tried to uninstall Libreoffice Base. Would not install. Tried to re-install both. No go.

No matter what I did to install, remove, purge. No go. Even with the "-f" switch using apt-get. 

Did recovery mode on reboot. Ran debpkg repair. Same errors again & again. 

All errors revolve around an "hsqldb-server" running with pid #nnnn or #nnn. 

The error:

ken@KensSSD120:~$ sudo apt-get remove -f hsqldb-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  hsqldb-server
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 125 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 225633 files and directories currently installed.)
Removing hsqldb-server ...
Exception in thread "main" java.lang.NoClassDefFoundError: org.hsqldb.jdbcDriver
   at java.lang.Class.initializeClass(libgcj.so.13)
   at java.lang.Class.forName(libgcj.so.13)
   at java.lang.Class.forName(libgcj.so.13)
   at org.hsqldb.util.RCData.getConnection(Unknown Source)
   at org.hsqldb.util.SqlTool.objectMain(Unknown Source)
   at org.hsqldb.util.SqlToolSprayer.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: java.sql.SQLFeatureNotSupportedException not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/usr/share/java/hsqldb.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.13)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.13)
   at java.lang.ClassLoader.loadClass(libgcj.so.13)
   at java.lang.ClassLoader.loadClass(libgcj.so.13)
   at java.lang.Class.forName(libgcj.so.13)
   at java.lang.Class.initializeClass(libgcj.so.13)
   ...5 more
WARNING:  hsqldb is still running!
invoke-rc.d: initscript hsqldb-server, action "stop" failed.
dpkg: error processing hsqldb-server (--remove):
 subprocess installed pre-removal script returned error exit status 1
There is already a hsqldb server running with pid 1879.
invoke-rc.d: initscript hsqldb-server, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 hsqldb-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
ken@KensSSD120:~$ 

Cannot install, remove or repair hsqldb-server. 

How to fix?

Thanks, guys!

Regards,

Ken Wagner

---

### Post by beaucoder2 on 2013-08-28
Hi Guys,

Solved the problem for the most part. 

The errors happening in the Libreoffice Base occurred using the most recent PPA setup for Base. The hsqldb-server did not install with it as it should have.

Running this latest version generated very odd behavior: It was not possible to shutdown because the hsqldb-server was still "running", i.e. a script could not find it. 

dpkg reported a severely disordered package. USC stopped working. 

Oy! Could not fix it. 

But wait!!  I remembered that the Ubuntu 13.04 install has a "Reinstall" option that preserves all User files. 

So, that's what I did. Worked like a charm. Before the reinstall I ran dpkg -l  (that's an 'ell') and directed the output to 'packages.txt.'

After the reinstall, all I had to do was add the missing packages back in. All their old data was right there again.

Greyed out icons were the first tip off. Old habits did the rest......hmmmmm......didn't I have 'Cherry Tree' here somewhere?

So, all is well once again. 

Best regards,

Ken Wagner

[LIST=1]
[*]Oh? What about LibreOffice Base? I will reinstall that again using the Ubuntu Main repository. Will let you know how it goes. Should be a few days.
[/LIST]

---

### Post by Richard_York on 2013-12-08
Hi, I think you're describing the problem I have. My trouble is that as I'm new to Linux, and definitely not up to playing with its nuts a bolts at all, I completely fail to understand your solution to your own problem!! 
On trying to register a database I get an error message saying that just that driver cannot be loaded, and giving "The additional driver class path is 'file:///usr [ and a very long string which I won't try and copy] "
Can you point me to an idiot's guide to knowing what to do with this, please?
Thanks!

---

