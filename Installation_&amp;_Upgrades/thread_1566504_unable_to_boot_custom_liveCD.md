---
title: "unable to boot custom liveCD"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by jibixbzh on 2010-09-02
[FONT=TimesNewRoman,Bold, serif][SIZE=3]Hello there,[/SIZE][/FONT]
  


  [FONT=TimesNewRoman,Bold, serif][SIZE=3]In order to let other colleagues try tools I use, I would like to build a customised live-DVD of Ubuntu. The goal is to incorporate two versions of the open-source command-line hydrodynamics software OpenFOAM within it. Traditionally, this software is designed to be installed in one's home directory, to be customised and enhanced easily. Hence the method I try to apply, based on [http://doc.ubuntu-fr.org/personnaliser_livecd](http://doc.ubuntu-fr.org/personnaliser_livecd) (in French, itself based on [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)) :[/SIZE][/FONT]
 
[LIST=1]
[*]     [FONT=TimesNewRoman,Bold, serif][SIZE=3]Build a first     modificated ubuntu live-iso with the stuff necessary for compilation     installed on it, i.e.:[/SIZE][/FONT]
[LIST=1]
[*]         [FONT=TimesNewRoman,Bold, serif][SIZE=3]extract the         official ubuntu iso and its squashfs filesystem,[/SIZE][/FONT]
[*]         [FONT=TimesNewRoman,Bold, serif][SIZE=3]chroot this         system to install the packages I need to compile OpenFOAM.[/SIZE][/FONT]
[*]         [FONT=TimesNewRoman,Bold, serif][SIZE=3]Add to the         <my_new_system>/etc/skel the source files of OpenFOAM,[/SIZE][/FONT]
[*]         [FONT=TimesNewRoman,Bold, serif][SIZE=3]Reconstruct the         squash filesystem and then the iso.[/SIZE][/FONT]
[/LIST]
 
[*]     [FONT=TimesNewRoman,Bold, serif][SIZE=3]Boot a virtual     machine with this iso, and [/SIZE][/FONT]
[LIST=1]
[*]         [FONT=TimesNewRoman,Bold, serif][SIZE=3]mount a         (virtual) device on the virtual ~/OpenFOAM folder[/SIZE][/FONT]
[*]         [FONT=TimesNewRoman,Bold, serif][SIZE=3]extract and         compile OpenFOAM in this folder, [/SIZE][/FONT]
[/LIST]
 
[/LIST]
 
[LIST=1]
[*]     [FONT=TimesNewRoman,Bold, serif][SIZE=3]Integrate these     files in the /etc/skel/ directory of the custom system, where the     personal files should be.[/SIZE][/FONT]
[/LIST]
 
[LIST=1]
[*]     [FONT=TimesNewRoman,Bold, serif][SIZE=3]rebuild a 2nd,     final, customised ubuntu system with that.[/SIZE][/FONT]
[/LIST]
  


  [FONT=TimesNewRoman, Bold, serif][SIZE=3]The scripts I wrote for that are attached to that post.[/SIZE][/FONT]
  [FONT=TimesNewRoman,Bold, serif][SIZE=3]I perform steps 1, 3, and 4 on a 2GB ram virtual machine with VirtualBox OSE, both guest and host being ubuntu 10.04 systems (32bits for guest while 64 for host, that is why I used a virtual machine).[/SIZE][/FONT]
  [FONT=TimesNewRoman,Bold, serif][SIZE=3]Step 2 is performed the same way, mounting a 6GB virtual hard disk ext4 partition on the /home/ubuntu/OpenFOAM folder of the virtual live machine, where OpenFOAM is compiled. Being on a live session, this is necessary for having enought disc space anyway (4 GB were used).[/SIZE][/FONT]
  


  [FONT=TimesNewRoman,Bold, serif][SIZE=3]Everything works perfect until the end of step 3: my first system runs OK with the whole added packages, the source files are situated in the right place. I can compile perfectly, and the obtained binaries work fine then on that virtual system.[/SIZE][/FONT]
  [FONT=TimesNewRoman,Bold, serif][SIZE=3]But when I try to boot the system I've built with those binaries added in, It doesn't work any more, due to group/user errors: [/SIZE][/FONT] 
 
[LIST=1]
[*]     [FONT=TimesNewRoman,Bold, serif][SIZE=3]1st     error: &#8220;GLib-WARNING **: getpwuid_r(): failed due to unknown user     id (0)&#8221;[/SIZE][/FONT]
[*]     [FONT=TimesNewRoman,Bold, serif][SIZE=3]The &#8220;Adding     live session user&#8221; step lasts a long time and finally fails,     displaying (see [http://ubuntuone.com/p/ESD](http://ubuntuone.com/p/ESD)):[/SIZE][/FONT]
[LIST]
[*]         [FONT=TimesNewRoman,Bold, serif][SIZE=3]groupdel: group         'ubuntu' does not exist [/SIZE][/FONT]
[*]         [FONT=TimesNewRoman,Bold, serif][SIZE=3]adduser:         'groupdel ubuntu' returned error code 6. Exiting. [/SIZE][/FONT]
[*]         [FONT=TimesNewRoman,Bold, serif][SIZE=3]usermod: user         'ubuntu' does not exist [/SIZE][/FONT]
[*]         [FONT=TimesNewRoman,Bold, serif][SIZE=3]install:         invalid user 'ubuntu' [/SIZE][/FONT]
[*]         [FONT=TimesNewRoman,Bold, serif][SIZE=3]install:         invalid user 'ubuntu' [/SIZE][/FONT]
[*]         [FONT=TimesNewRoman,Bold, serif][SIZE=3]Done[/SIZE][/FONT]
[/LIST]
 
[/LIST]
  


 
[LIST=1]
[*]     [FONT=TimesNewRoman,Bold, serif][SIZE=3]Then I have a     lot of &#8220;sudo: unknown user: ubuntu&#8221; errors (see     [http://ubuntuone.com/p/ESE](http://ubuntuone.com/p/ESE))[/SIZE][/FONT]
[*]     [FONT=TimesNewRoman,Bold, serif][SIZE=3]After that,     &#8220;init: ureadahead-other main process (XXX) terminated with status     4&#8221; errors (where XXX takes its value in 845 846 and maybe more     (see [http://ubuntuone.com/p/ESG](http://ubuntuone.com/p/ESG)).[/SIZE][/FONT]
[*]     [FONT=TimesNewRoman,Bold, serif][SIZE=3]Then, instead of     being automatically logged in, I have a log-in screen but without     any user (see [http://ubuntuone.com/p/ESH](http://ubuntuone.com/p/ESH)).     It sounds logical since the &#8220;ubuntu&#8221; user couldn't be created.     I've tried to log in as root (and &#8220;ubuntu too&#8221;) but didn't     manage to.[/SIZE][/FONT]
[*]     [FONT=TimesNewRoman,Bold, serif][SIZE=3]If I go to a     tty, since it's expected to log-in itself, I just have an     &#8220;Authentication failure&#8221; list :-s (see     [http://ubuntuone.com/p/ESI](http://ubuntuone.com/p/ESI))[/SIZE][/FONT]
[/LIST]
  [FONT=TimesNewRoman,Bold, serif][SIZE=3]As indicated in [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization), I've checked for uid > 999 and I had one so I changed it to 500:[/SIZE][/FONT]

 root@lucid32-virtual:/# awk -F: '$3 > 999' /etc/passwd  
 nobody:x:65534:65534:nobody:/nonexistent:/bin/sh 
 root@lucid32-virtual:/# awk -F: '$3 == 1' /etc/passwd  
 daemon:x:1:1:daemon:/usr/sbin:/bin/sh 
 root@lucid32-virtual:/# awk -F: '$3 == 500' /etc/passwd  
 root@lucid32-virtual:/# usermod -u 500 nobody  
 root@lucid32-virtual:/# awk -F: '$3 > 999' /etc/passwd  
 root@lucid32-virtual:/# awk -F: '$3 == 500' /etc/passwd nobody:x:500:65534:nobody:/nonexistent:/bin/sh 
 root@lucid32-virtual:/# awk -F: '$4 > 999' /etc/passwd  
 sync:x:4:65534:sync:/bin:/bin/sync  
 nobody:x:500:65534:nobody:/nonexistent:/bin/sh 
 kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false  
 sshd:x:115:65534::/var/run/sshd:/usr/sbin/nologin 

  [FONT=TimesNewRoman,Bold, serif][SIZE=3]but that didn't solve the problem, so I also changed the corresponding gid:[/SIZE][/FONT]

 root@lucid32-virtual:/# usermod -g500 -u500 nobody  
 usermod: el grupo «500» no existe  
 according to [http://it.toolbox.com/blogs/locutus/how-to-change-a-users-uid-and-gid-26368](http://it.toolbox.com/blogs/locutus/how-to-change-a-users-uid-and-gid-26368) I changed the group ID 65534 to 500 editing directly the /etc/group file:
 root@lucid32-virtual:/etc# nano group  
 root@lucid32-virtual:/# awk -F: '$4 > 999' /etc/passwd  
 sync:x:4:65534:sync:/bin:/bin/sync  
 nobody:x:500:65534:nobody:/nonexistent:/bin/sh 
 kernoops:x:109:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false  
 sshd:x:115:65534::/var/run/sshd:/usr/sbin/nologin 
 root@lucid32-virtual:/etc# usermod -g500 -u500 nobody  
 root@lucid32-virtual:/etc# usermod -g500 sync  
 root@lucid32-virtual:/etc# usermod -g500 kernoops  
 root@lucid32-virtual:/etc# usermod -g500 sshd  
  [FONT=TimesNewRoman,Bold, serif][SIZE=3]
but it didn't change anything either :-s[/SIZE][/FONT]
  


  [FONT=TimesNewRoman,Bold, serif][SIZE=3]I have found a few problem a bit similar on the web:[/SIZE][/FONT]
  [FONT=TimesNewRoman,Bold, serif][SIZE=3]-> one without  a lot of details neither any solution ([http://ubuntuforums.org/showthread.php?t=1469704&highlight=sudo%3A+unknown+user%3A+ubuntu]("http://ubuntuforums.org/showthread.php?t=1469704&highlight=sudo%3A+unknown+user%3A+ubuntu")) [/SIZE][/FONT] 
  [FONT=TimesNewRoman,Bold, serif][SIZE=3]-> other in a post about ubuntu 10.04 boot bugs ([http://ubuntuforums.org/showthread.php?t=1465768&highlight=sudo%3A+unknown+user%3A+ubuntu](http://ubuntuforums.org/showthread.php?t=1465768&highlight=sudo%3A+unknown+user%3A+ubuntu)), but the mentioned solution (booting in with acpi=off and noapic) didn't work for me :-s[/SIZE][/FONT]
  


  [FONT=TimesNewRoman,Bold, serif][SIZE=3]I tried a few times changing details but always get this same behaviour. It works adding other kind of files in the skel dir, such as the source files, but doesn't work with the compiled stuff. I can't understand why...[/SIZE][/FONT]

  [FONT=TimesNewRoman,Bold, serif][SIZE=3]does anyone has an idea ?[/SIZE][/FONT]

---

### Post by barinov2000 on 2010-09-28
have you tried REMASTERSYS?
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
latest version for karmic also works in lucid :)

---

### Post by jibixbzh on 2010-09-28
No, I hadn't, thanks for the link!

---

