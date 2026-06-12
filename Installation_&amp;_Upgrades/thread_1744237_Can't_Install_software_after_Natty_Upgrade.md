---
title: "Can't Install software after Natty Upgrade"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by jackn on 2011-04-30
Asus laptop.

I've just upgraded to Natty, and am overall happy with it.

I've found out, however that software handling was broken.
When I try to install any software, I get:
"unable to securely remove... linux-headers-2.6.35-23-generic"

I had a message about this during the upgrade.
I've also tried apt-get 'clean' or 'autoclean', to no avail.

What can I do to fix this?

Jackn

---

### Post by Rubi1200 on 2011-04-30
What errors are reported when you run this command:

```
sudo dpkg --configure -a
```

Please post the exact error so we can help you troubleshoot this issue.

Thanks.

---

### Post by jackn on 2011-04-30
Thank you for helping out, Rubi.

In answer to your question, in the terminal I get nothing:
```
jackn@$:~$ sudo dpkg --configure -a
[sudo] password for jackn: 
jackn@$:~$ 
```

In addition, when launching software management off the sidebar (Natty, Unity), I get:
"Items cannot be installed or removed until the package catalog is repaired."
When I ask it to go ahead and repair the catalogue, it announces failure, and in 'details', I get:
[INDENT]Removing linux-headers-2.6.35-23-generic ...

dpkg: error processing linux-headers-2.6.35-23-generic (--remove):

 unable to securely remove '/usr/src/linux-headers-2.6.35-23-generic/include/config/fw/loader.h': Not a directory

No apport report written because MaxReports is reached already
Errors were encountered while processing:

 linux-headers-2.6.35-23-generic[/INDENT]

I don't know whether it's helpful.
I'll be glad to try out further advice.

Thanks,
jackn

---

### Post by Rubi1200 on 2011-04-30
Hi,

post the output of this command from the terminal please:

```
ls /boot/vmlinuz*
```

---

### Post by jackn on 2011-04-30
Thanks again, Rubi.

Here you go:
```
jackn@$:~$ ls /boot/vmlinuz*
/boot/vmlinuz-2.6.32-25-generic  /boot/vmlinuz-2.6.38-8-generic
/boot/vmlinuz-2.6.35-28-generic
```


jackn

---

### Post by Rubi1200 on 2011-04-30
Okay, this is what you appear to have:

2.6.38-8 Natty
2.6.35-28 Maverick
2.6.32-25 I assume this is probably Lucid

So, this what I would do:

Go into Synaptic Package Manager and search for and remove that header file that is causing the problem then run > sudo apt-get update in the terminal. Hopefully this will resolve the issue.

---

### Post by jackn on 2011-04-30
OK Rubi.

Tried to remove the offending headers with Synaptic.

Here's what Synaptic came up with:
[INDENT]E: linux-headers-2.6.35-23-generic: unable to securely remove '/usr/src/linux-headers-2.6.35-23-generic/include/config/fw/loader.h': Not a directory[/INDENT]

To sum it up: These piece of software can't be removed, and as a result, all package management is broken.
Synaptic explains that the reason is that the address listed is not a directory.
When I try to list it, I only get:
```
jackn@$:~$ ls /usr/src/linux-headers-2.6.35-23-generic/include/config/fw 
/usr/src/linux-headers-2.6.35-23-generic/include/config/fw
```

So, to me, 'fw' is a file, and I don't know where 'fw/loader.h' comes from.

Indeed, it looks like something has gone awry is.
When I do the same with another version of the kernel:
```
jackn@$:~$ ls /usr/src/linux-headers-2.6.38-8-generic/include/config/fw/loader.h 
/usr/src/linux-headers-2.6.38-8-generic/include/config/fw/loader.h
```

So, for some reason, the headers which cannot be removed are different from the usual structure, and cannot be handled.

In the meantime, I've found a [thread]("https://answers.launchpad.net/ubuntu/+source/apt/+question/140716") on launchpad with a 
suggestion:
[INDENT]Problem solved by moving the error files from the location and then making directory which is supposed to be removed by the update manager.
for example
/usr/src/linux-headers-2.6.31-20/arch/mips/fw/sni/Makefile
was not existing because fw is a file in the above path so whole path becomes irrelevent, i moved the fw from the mips folder to src folder then created the dir by
$sudo mkdir -p /usr/src/linux-headers-2.6.31-20/arch/mips/fw/sni/Makefile
there after ran sudo apt-get autoremove to see the result...and it came out on top...Thanks Actionparsnip who gave the idea of creating the file but it was not getting created that was the little hiccup as two same names can not coexist in the same folder in the above path fw file name and folder name which was cause of the problem.
Thanks again[/INDENT]

So, I'm trying this, and will report.

---

### Post by jackn on 2011-04-30
Worked...

I actually had to deal with three files (fw, the first one Synaptic ran into and stopped at, module, and hmac). Each one was expected to be a directory, with a file in it.
I followed the procedure suggested above on Launchpad.
The following gives the necessary details.

First, I moved the files above to /usr/src/.
Then, I could create directories with the same names.
Finally, using 'touch', I created the files expected within those directories (in the case of 'fw', for example, the expected file was 'loader.h').
At this point, apt-get autoremove could finally work.
I then manually removed each one of the files (which were supposed to be directories and had stood in the way) previously moved to /usr/src/.

Indeed, once 'autoremove' worked, I was also able to install a piece of software I was interested in.

Hope this is both clear enough and not too long.

Thank you so much, Rubi, for the attention and help.

jackn

---

### Post by Rubi1200 on 2011-04-30
Excellent, I am really pleased you got this sorted out.

And, you are welcome for the help of course :-)

Enjoy!

---

