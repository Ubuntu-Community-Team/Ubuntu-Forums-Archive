---
title: "Grub after installation"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by edhorsman on 2012-05-15
I have been using ver 11.04, 64 bit. It was installed on a Lexar 16 GB stick drive and it worked fine. I recently accepted upgrades and it failed to boot after that. I then downloaded 12.04 64 bit, burned it to a CD and installed on the Lexar. Selected complete format to erase all data during install. All it will now do is give me a GRUB screen and not boot. I repeated the procedure to re-install it 3 times with the same results. What is the problem?

---

### Post by VMC on 2012-05-15
Download bootinfoscript(click on my blue link), then run as root. Results will be in RESULTS.txt file.

Then we can determine what needs fixing.

---

### Post by edhorsman on 2012-05-16
> **VMC said:**
> Download bootinfoscript(click on my blue link), then run as root. Results will be in RESULTS.txt file.
 
Then we can determine what needs fixing.
 
I am presently running Windows 7.  Is it ok to run this with this operating system, and I do not understand what you mean by run as root.  Is this something I do in the grub prompt or in windows command propmpt?  Thanks for your help.

---

### Post by wilee-nilee on 2012-05-16
> **edhorsman said:**
> I am presently running Windows 7.  Is it ok to run this with this operating system, and I do not understand what you mean by run as root.  Is this something I do in the grub prompt or in windows command propmpt?  Thanks for your help.

The script has to be run on a live Ubuntu cd or install, boot a live cd and run these commands, and the reults text will be in home in ubuntu. Copy and paste all the text to a reply.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
``````
chmod a+x bootinfoscript
``````
sudo bash bootinfoscript
```

---

### Post by carl4926 on 2012-05-16
It a linux script
Boot Ub live cd and do it

or use this:
[http://ubuntu-rescue-remix.org/Download](http://ubuntu-rescue-remix.org/Download)

---

