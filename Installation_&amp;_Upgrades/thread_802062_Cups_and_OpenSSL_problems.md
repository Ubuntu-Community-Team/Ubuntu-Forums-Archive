---
title: "Cups and OpenSSL problems"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by xueg0i on 2008-05-21
At my university I have to print via a Windows server which requires ssl. In Gutsy I followed [_this guide_]("http://www.cse.ust.hk/~lkmpoon/linux/ubuntu-hkust.html"). That worked well. However after upgrading to Hardy another version of cups got installed. I tried the above guide again, but to no avail. The problem lies with building the package. Most of it looks ok (e.g. the compiling part), but at the end I get a message that two test procedures failed:
```
2 tests failed.
Log files can be found in /tmp/cups-root/log.
A HTML report was created in /tmp/cups-root/cups-str-1.3-2008-05-21-root.html.
```
This prevents the package from being finalized and build. I will attach the output from dpkg-buildpackage.


[SIZE="3"]_Question:_[/SIZE] Does anyone know why this method fails, because I cannot see any hint in the output generated.


Quick 'n Dirty fix:

Get required packages and source:
```
sudo apt-get build-dep cupsys
sudo apt-get install libssl-dev
sudo apt-source cupsys
```
Compile and install cups (replace 1.x.xx by the right version number):
```
cd cupsys-1.x.xx
./configure --enable-openssl
make && sudo make install
```
Make a link to the right backend:
```
sudo ln -s /usr/lib/cups/backend/ipp /usr/lib/cups/backend/https
```
Restart the cups server:
```
sudo /etc/init.d/cupsys restart
```

Now you should be able to print to printservers which require openssl. But remind that this is a 'dirty' fix and might break things during future upgrades of cups.

---

### Post by dstew on 2008-05-21
> Does anyone know why this method fails, because I cannot see any hint in the output generated.The output is telling you to look in the log files for the information on the error. Just open the file /tmp/cups-root/cups-str-1.3-2008-05-21-root.html in your internet browser. Also, look in /tmp/cups-root/log for log files.

---

### Post by xueg0i on 2008-05-21
Thanks for the suggestions, though I'm not a noob. Looked at the log files, but everything which is in that html file is also in the output I attached. I did find two FAILs, but there's no information with it that can point me in the right direction.

```
Test Summary

PASS: Printer 'Test1' correctly produced 55 page(s).
PASS: Printer 'Test2' correctly produced 23 page(s).
PASS: 153 requests processed.
PASS: 0 emergency messages.
PASS: 0 alert messages.
PASS: 0 critical messages.
[COLOR="Red"]FAIL[/COLOR]: 0 error messages, expected 9.
PASS: 0 warning messages.
PASS: 0 notice messages.
PASS: 1 info messages.
[COLOR="Red"]FAIL[/COLOR]: 0 debug messages, expected more than 0.
PASS: 0 debug2 messages.
```

---

### Post by dstew on 2008-05-21
Sorry! I didn't notice the attachment...

The "failures" sound like there wasn't enough trouble during the installion. It expected 9 error messages but didn't get any? I don't see why that would be a problem. And the other "failure", no debug messages, goes along with that. If you didn't get any errors, why would you get a debug message? Anyway, it seems that CUPS should be installed and working based on your story, and the log output. You are right, that when you upgrade later, since the CUPS was hand-installed, CUPS will not be upgraded.

I am curious why you had to do this in the first place. Did you try to do the internet printing after your Hardy upgrade? Did you get the IPP error? It seems that the Hardy [cupsys]("http://packages.ubuntu.com/hardy/net/cupsys") package has ssl and IPP support...

---

### Post by xueg0i on 2008-05-21
Dstew, I completely agree with your analysis. To be honest, I don't exactly now when what happened. When I upgraded to Hardy, ipp printing stopped working. I didn't have time to look into it before last weekend. This weekend I felt like trying Fedora 9, that was a disaster, so I did a fresh Hardy install (64bit) afterwards.

Fresh Hardy, no ipp printing at the university. I know SSL is enabled by default, but no dice. So I assume upgrading to Hardy had been the trouble in the first place. As far as I know I didn't get any ipp errors. Cups kept complaining about the server URI that started with [https://.](https://.) Even manually linking the https backend to the ipp backend didn't help. Only enabling openssl solved the problem.

Oh, and the system administrators are giving me a hard time since they know **** about linux. That also doesn't help ;)

---

### Post by egbert on 2009-10-06
Hi xueg0i, I would like to add to this post that I'm experiencing exactly the same issues. I also get:

PASS: Printer 'Test1' correctly produced 55 page(s).
PASS: Printer 'Test2' correctly produced 23 page(s).
PASS: 274 requests processed.
PASS: 0 emergency messages.
PASS: 0 alert messages.
PASS: 0 critical messages.
FAIL: 0 error messages, expected 9.
PASS: 0 warning messages.
PASS: 0 notice messages.
PASS: 1 info messages.
FAIL: 0 debug messages, expected more than 0.
PASS: 0 debug2 messages.

Have you found a solution yet? 

I would really like to know since I need Cups with SSL support to print at the university too.

Best, Egbert

---

### Post by HandleWithCare on 2010-09-09
It's an old post, but I am experiencing the exact same problem under 10.04
Any clues on how to fix this yet?

---

