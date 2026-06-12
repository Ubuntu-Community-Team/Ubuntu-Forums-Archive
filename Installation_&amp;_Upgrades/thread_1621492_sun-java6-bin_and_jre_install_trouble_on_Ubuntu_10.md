---
title: "sun-java6-bin and jre install trouble on Ubuntu 10.10"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by bjbraams on 2010-11-14
Greetings. I'm struggling to upgrade my sun-java6-bin and sun-java6-jre on my Ubuntu 10.10 desktop. The package seems to have gotten into a corrupted state; I can't remove or purge it (sudo apt-get) and can't upgrade or install it either. I think I need to 'rm -rf' some directories and then install again, but I don't know which directories to remove; java seems to exist in multiple locations including /etc, /usr/bin, /usr/lib, /var/lib and multiple subdirectories thereof. I would appreciate advice about cleaning up the bad state.

Some more detail, copies of error messages, follow:

When I try 'sudo apt-get remove' (either sun-java6-bin or sun-java6-jre) I get finally this response:
dpkg: error processing sun-java6-bin (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
dpkg: error processing sun-java6-jre (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.

Trying 'sudo apt-get install sun-java6-bin':
Selecting previously deselected package sun-java6-jre.
(Reading database ... 
dpkg: warning: files list file for package `sun-java6-jre' missing, assuming pac
kage has no files currently installed.
(Reading database ... 60%
(Reading database ... 137645 files and directories currently installed.)
Preparing to replace sun-java6-jre 6.22-0ubuntu1~10.10 (using .../sun-java6-jre_
6.22-0ubuntu1~10.10_all.deb) ...

Trying 'sudo aptitude install sun-java6-bin':
The following packages will be upgraded: 
  sun-java6-bin 
1 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 88.4MB will be used.
Do you want to continue? [Y/n/?] 
E: I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.
E: I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

Trying 'sudo aptitude purge sun-java6-jre':
The following packages will be REMOVED:  
  sun-java6-jre{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] 
E: I wasn't able to locate file for the sun-java6-bin package. This might mean you need to manually fix this package.
E: I wasn't able to locate file for the sun-java6-bin package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

---

### Post by 73ckn797 on 2010-11-14
Try looking here:
```
/var/cache/apt/archives
```
And delete all *.deb files

The terminal command will be:
```
sudo apt-get clean
```

This will clear out all downloaded packages.

---

### Post by bjbraams on 2010-11-14
Thank you 73ckn797. There were lots of *.deb files, and the 'sudo apt-get clean' command got rid of them. But my sun-java6-{bin,jre} install/reinstall/upgrade still fails. When I try to remove or purge them I get the same error messages as before. The install process gives similar error messages too. Finally, when I do install (either apt-get or aptitude) the command terminal gets take over by a Sun license agreement. It has a blue border, light grey background, black text, and a header that says: "Package configuration" and "Configuring sun-java6-jre". Then follows a 14-point agreement.
I am totally happy to sign on the dotted line, click my approval, or do whatever is required. It is mysterious what I'm supposed to do, but a Google search tells me that I should hit return. Fine, I hit return. Then the system just hangs. It doesn't respond to ctrl-c or anything. After 30 minutes or so I just kill the window.

Before killing it this time I do a 'ps -la' in a different window. It shows the following:
$ ps -la
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0  2217  2027  0  80   0 -  6487 poll_s pts/0    00:00:01 apt-get
0 S  1000  2218  2027  0  80   0 -   972 pipe_w pts/0    00:00:00 tee
0 S     0  2268  2261  0  80   0 -  2966 pipe_w pts/1    00:00:01 frontend
0 S     0  2275  2268  0  80   0 -   475 pipe_w pts/1    00:00:00 preinst
0 S     0  2277  2268  0  80   0 -  1557 poll_s pts/1    00:00:00 whiptail
0 R  1000  2787  2697  0  80   0 -  1094 -      pts/2    00:00:00 ps

Maybe this helps to identify what process is hanging. Also I have a record of the messages from the install command before it popped up the license agreement and hung.

Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  sun-java6-jre
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming
The following packages will be upgraded:
  sun-java6-bin sun-java6-jre
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 36.1MB of archives.
After this operation, 103MB of additional disk space will be used.
Do you want to continue [Y/n]? Get:1 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner sun-java6-jre all 6.22-0ubuntu1~10.10 [6,420kB]
Get:2 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner sun-java6-bin i386 6.22-0ubuntu1~10.10 [29.7MB]
Preconfiguring packages ...
Fetched 36.1MB in 44s (814kB/s)
Selecting previously deselected package sun-java6-jre.
(Reading database ... 
dpkg: warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.

I'm hoping for further advice. Maybe I need to do forcibly remove some directories, but then I don't know which ones to remove.

---

### Post by wildanimal on 2010-12-09
I had a bad experience trying to get Sun Java 6.22 working.
After installing it I checked with java.com and it told me I had version 6 still. My solution came after two days of trying different things. I eventually figured out I had to uninstall all java from Ubuntu Software Center, this included OpenJava and all Sun java installations. this also means a bunch of other programs get installed too. I verified that no java was installed with java.com again. This time I received the message that java was missing. WooHoo! I then added all sources in update manager, and installed all updates to my system. I then installed Sun Java by using Ubuntu Software Center, clicking on Get Software selecting Canonical Partners, searched for Sun Java, and installed the one that was architecture independent. Success! I checked back with java.com and this time it reported I had the latest jave, 6.22 installed. All that just to get pogo.com working, well that and a ton of other applications that want the latest Sun java installed, OpenJava despite being pushed for adoption still has problems. I wish that Ubuntu wouldn't let Oracle dictate what java gets installed by default. Just from the number of posts on the net it seems that a lot of other people adopting ubuntu 10.10 are having java problems. I hope this helps.

---

### Post by mick222 on 2010-12-09
make sure partner repository is enabled in software sources . Open synaptic search for java remove all entries +iced tea then try to reinstall sun java from synaptic

---

### Post by oldos2er on 2010-12-09
> **bjbraams said:**
>  Finally, when I do install (either apt-get or aptitude) the command terminal gets take over by a Sun license agreement. It has a blue border, light grey background, black text, and a header that says: "Package configuration" and "Configuring sun-java6-jre". Then follows a 14-point agreement.
I am totally happy to sign on the dotted line, click my approval, or do whatever is required. It is mysterious what I'm supposed to do, but a Google search tells me that I should hit return. Fine, I hit return. Then the system just hangs. It doesn't respond to ctrl-c or anything. After 30 minutes or so I just kill the window.


To navigate in the ncurses screen, use Tab or arrow keys to move around, highlight 'Ok' then press Enter. The install should continue.

I would run```
sudo apt-get update
``` first.

---

### Post by Mickser_52 on 2011-01-16
I found this thread because I too cannot get sun-java6 to install. I have had the same experiences as others when I tried. After a long download time the licence agreement appeared in the terminal window and nothing happened no matter how I tried to highlight the OK at the bottom of the screen.

No solution from me I'm afraid but I would like to keep the thread alive in the hope that someone may have found a solution since the previous post

---

### Post by oldos2er on 2011-01-16
Do you mean your keyboard is not responding at all when the license agreement comes up?

---

### Post by Mickser_52 on 2011-01-16
Thanks for reply.

The keyboard worked perfectly. I could scroll up and down the licence agreement but nothing would highlight the OK on the screen, pressing return had no effect and in the end I used control-d to exit back to the terminal. After that it took a lot of research to remove and free up the update and upgrade commands which were giving error messages.

The good news is.. I managed to download it successfully using Ubuntu Software Center but I have not had time to test it yet.

---

### Post by Mickser_52 on 2011-01-16
Thanks for reply.

The keyboard worked perfectly. I could scroll up and down the licence agreement but nothing would highlight the OK on the screen, pressing return had no effect and in the end I used control-d to exit back to the terminal. After that it took a lot of research to remove and free up the update and upgrade commands which were giving error messages.

The good news is.. I managed to download it successfully using Ubuntu Software Center but I have not had time to test it yet.

---

### Post by oldos2er on 2011-01-16
Usually the Tab or arrow keys will highlight and/or move the cursor around in an ncurses interface (for a US keyboard, anyway). Not sure why they're not working for you.

---

### Post by outcast247 on 2011-08-21
Hi, bjbraams
I tried the following method & it worked.You said when you try to reinstall within few seconds terminal gets take over by a Sun license agreement.that happend to me as well plus for me i cannot install or uninstall any package.. you can fix it like this:
Go to synaptic manager & search in the box by typing sun-java6-jre
or sun-java6-bin..select enyone of it,go to edit tab on the top & fix broken packages , press ok to upgrade then go to apply on the top..within few seconds a box will appear saying you have to agry the license the select ok...thats it now both sun-java6-jre & sun-java6-bin will be fixed.....

---

