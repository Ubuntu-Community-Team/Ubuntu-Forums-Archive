---
title: "Getting JRE to work???"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by dm64 on 2006-07-28
Hi

Im still a bit of a novice with Linux/Ubuntu and I am trying to get JRE working with Firefox with no luck.

Obviously Im missing something LOL

It seems to be installed in Ubuntu but Firefox prompts me to install the "missing plugin" - when I do this it prompts me the do a manual install, which I have previously done.

Below  are some of the command line info that I have - I hope it might help someone point me in the right direction.

Thanks in advance!!!
Dennis





dennis@ubuntu:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
sun-j2re1.5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

and

dennis@ubuntu:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2re1.5-sun/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/j2re1.5-sun/bin/java' to provide `java'.

---

### Post by dtfinch on 2006-07-29
You'll need to create a symbolic link to the java plugin in your firefox plugins directory. [http://www.ubuntuforums.org/showthread.php?t=39555](http://www.ubuntuforums.org/showthread.php?t=39555)

Something like:
ln -s /wherever-you-installed-java/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins

---

### Post by dm64 on 2006-07-29
Hey thanks for the info

Unfortunately Im still having problems, this is what I got when I issued those commands

dennis@ubuntu:/usr/lib$ ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/pluginsln: creating symbolic link `/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so' to `/usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so': Permission denied

I redownloaded the package based on the info in the link you supplied but fell at the first hurdle

dennis@ubuntu:/usr/lib$ cd ~/Desktop
dennis@ubuntu:~/Desktop$ sudo ./jre-1_5_0_06-linux-i586.bin
sudo: ./jre-1_5_0_06-linux-i586.bin: command not found
dennis@ubuntu:~/Desktop$ sudo ./jre-1_5_0_06-linux-i586.bin
sudo: ./jre-1_5_0_06-linux-i586.bin: command not found
dennis@ubuntu:~/Desktop$
dennis@ubuntu:~/Desktop$


Im totally lost now so I think I will just do Java stuff on my windows machine - which is a shame I like Linux/Ubuntu but its difficult to work out when things dont work as they should :(

---

### Post by kerry_s on 2006-07-29
Dude you got to do the link with sudo->

sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins

---

### Post by dm64 on 2006-07-29
Thanks for the reply Kerry...much appreciated!

Unfortunately this stil gives me an issue

dennis@ubuntu:~$ sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins
ln: `/usr/lib/mozilla-firefox/plugins/libjavaplugin_oji.so': File exists


File exists?? Firefox still doent recognise the plug-in...it seems to be installed and the link is there but....????

---

