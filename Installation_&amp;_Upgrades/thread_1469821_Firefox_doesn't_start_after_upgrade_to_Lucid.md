---
title: "Firefox doesn't start after upgrade to Lucid"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by galoisgalois on 2010-05-02
Hi,

I upgraded to Lucid fro Karmic last night and Firefox is not starting (not even in safe mode). I tried with complete removal and reinstall but no change in behavior.

When I invoke Firefox command from terminal I get this error message: 


galois@galois-desktop:~$ firefox
MozPlugger: Error: Too many types (32) for handler 20 (application/vnd.sun.xml.writer:sxw:OpenOffice Writer 6.0 documents)
galois@galois-desktop:~$ 

Please advice.

Thank you.

---

### Post by davidmohammed on 2010-05-02
try starting firefox with

firefox -ProfileManager

and create a new profile when prompted

---

### Post by galoisgalois on 2010-05-02
I created a new profile and I still get the same error.

galois@galois-desktop:~$ firefox -ProfileManager
MozPlugger: Error: Too many types (32) for handler 20 (application/vnd.sun.xml.writer:sxw:OpenOffice Writer 6.0 documents)
galois@galois-desktop:~$ 


Thank you.

---

### Post by galoisgalois on 2010-05-02
I think I solved the problem by commenting the lines for OpenOffice plugins the file mozpluggerrc. For me, I found this file at /etc/. 

After commenting this and relaunching firefox resulted into an error with libmoon. 

Attempting to load the system libmoon 
Segmentation fault

I removed libmoon using sudo apt-get remove libmoon (or you can use Synaptic). Firefox started without any problems and the previous firefox profiler was restored too.

Thank you.

---

