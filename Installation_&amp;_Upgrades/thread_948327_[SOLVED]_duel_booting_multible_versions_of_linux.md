---
title: "[SOLVED] duel booting multible versions of linux"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by fewjr on 2008-10-15
Hello All,
     I have been trying to teach myself how to install more than one distro of linux on one computer/hard drive. I am trying a method I read from these two links:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)

I installed Ubuntu hardy heron using guided>use whole disk. Then I ran gparted live cd and resized my ubuntu partition to make room for others. This is what I have:

/dev/hda1 ext3 7.84GB boot
/dev/hda2 extended 10.80GB
    /dev/hda7 ext2 101.91MB (for dedicated GRUB partition)
    /dev/hda6 ext3 9.88GB  (for future installs of other distros)
    /dev/hda5 SWAP 839.30MB

It makes sense to me to use the dedicated GRUB partition method. So when I boot into ubuntu and open a terminal I do:
```
 sudo mkdir /media/GRUB
Password: my password
herman@red:~$ sudo mount -t ext2 /dev/hda7 /media/GRUB/

```

It makes the directory just fine, but the second command says that special device /dev/hda7 doesn't exist or something to that effect. Can anyone help me to see what I am doing wrong? I do not have windows on this machine. I would just like to figure out how to do this right before I move on. Thanks in advance.

Regards,
fewjr

---

### Post by fewjr on 2008-10-16
Bump please:-\"

---

### Post by kellemes on 2008-10-16
Assuming the distributions you use are making use of Grub (this instead of LILO). I use Ubuntu and Mepis as examples..

You need to figure out a partition scheme.. this is highly personal so I can't give you a howto. It doesn't really matter as long as both distro's have there own space. I tend to create my partition scheme before I start installing anything, this can be done using a live-system or something like GParted-Livecd.
Give both distro's there own partition(s).. the only partition both distro's can share is /swap

You need to make a decision about the distribution you want to manage Grub from.. assuming this is Ubuntu.. simply install Ubuntu and have it install Grub.
Now you install Mepis, let it install Grub, it will overwrite the MBR.. not your Grub /boot/grub/menu.lst from the Ubuntu install.
Now you can use [Super Grub Disk]("http://www.supergrubdisk.org/") (download/burn/boot) to resetup Grub based on the Ubuntu's /boot/grub/menu.lst. So have SGD "fix" Grub by pointing to the partition where you installed Ubuntu's "menu.lst".
Now you have your old/first Grub bootmenu back, but without the entry to Mepis, how to fix it..
Add an entry to your /boot/grub/menu.lst (the Ubuntu one, since I assume this is where you want to manage Grub from) like so..
```
# Mepis
title Mepis
configfile   (hd2,8)/grub/menu.lst
```
The configfile entry should point to the location of /boot/grub/menu.lst of your Mepis-install, so it will be different in your case.
This way you get a nested bootmenu, works great.

You can have as many distro's installed as you wish.


******************************

When you want to install a distro that makes use of LILO instead of Grub (like Zenwalk), you simply install LILO in the root-partition of Zenwalk (so not the MBR!) and chainload like so..

```
# Zenwalk
title Zenwalk
root (hd*,*)
chainloader +1
```

---

### Post by louieb on 2008-10-16
Just want to make sure /dev/sda7 is there. Please post the partition table.

```
sudo fdisk -l
``` lowercase L at the end

I use a dedicated GRUB partition also. Think you'll like it once you get it set up correctly.

---

### Post by Herman on 2008-10-16
:) Hello fewjr, and also kellemes and louieb and everyone else,

Thank you, fewjr, for your post about your problems with trying to follow my how-to called '[How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").'
Thanks to your post, I took another look at that how-to and realized it was a little hard to follw and not only that, it was out of date. Things in Ubuntu are now a lot easier than when that how-to was made. 

I have re-written it and made quite a lot of changes. 
If you like, you should start again.
I hope it will be a lot easier now.

You can copy and paste the commands, but you'll probably need to alter some parts of some of the commands to suit your own set-up.
You shouldn't copy the 'user@hostname' part of the commands, I just included that part for an example, hoping it would be easier for new users.
```
[COLOR=Red]**herman@red:~$**[/COLOR] sudo mount -t ext2 /dev/hda7 /media/GRUB/
```Actually, you won't even need to use that command at all anymore. (Unless you're using an old version of Ubuntu).

Regards, Herman :)

---

### Post by fewjr on 2008-10-17
Hello Fellas,
     I really appreciate you guys responding. It was nice to get an answer so soon on this. Actually, I just finished reinstalling Ubuntu8.04.1 a little while ago. I used Guided>use entire disc. I then ran gparted-live cd and resized Ubuntu partition and added more partitions. This is what I have now:

/dev/hda1 ext3 6GB boot (Ubuntu here)
/dev/hda2 SWAP 1GB
/dev/hda3 Extended 11.64GB
/dev/hda5 ext3 5.86GB   (Mandriva here)
/dev/hda6 ext3 5.78     (next distro)

The thing is, when I installed Mandriva, I was given the options to format what partition I wanted. I chose /dev/hda5 set to /. When it was time to install GRUB during this install I chose to install it to the Mandriva partition instead of the others. I didn't see MBR in the list. I may have this wrong. I have been having trouble understanding where to put what in all this confusion, like when you do a manual install instead of guided. Anyway, I got a prompt that said "these are the kernels in grub now or something like that. Ubuntu was there. So now I have this computer booting both installs from GRUB, except that GRUB is being run from /dev/hda5. I still have some comprehending to do..lol. I'm going to try to change things around to see if I can. Then I'm going back to try the Dedicated partition method. Here are the menu.lst files:
UBUNTU:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3b4b3553-7b3c-4063-b938-7e6d3590928c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3b4b3553-7b3c-4063-b938-7e6d3590928c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3b4b3553-7b3c-4063-b938-7e6d3590928c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```


Mandriva:

```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/boot/gfxmenu
default 0

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=760acc10-1f49-45e0-ba6f-9885b59ab482  resume=/dev/hda2 splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

title linux-nonfb
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=760acc10-1f49-45e0-ba6f-9885b59ab482  resume=/dev/hda2
initrd (hd0,4)/boot/initrd.img

title failsafe
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=760acc10-1f49-45e0-ba6f-9885b59ab482  failsafe
initrd (hd0,4)/boot/initrd.img

title Ubuntu 8.04.1 
root (hd0,0)
configfile /boot/grub/menu.lst

```

As you can see, only the configfile (/boot/grub/menu.lst) is mentioned for Ubuntu to boot from Mandriva's menu.lst. When GRUB comes up upon booting I don't get the choices for Ubuntu's recovery mode or memtest in the GRUB kernel list. This is like you mentioned in your post kellemes, only from the second distro install.

So I am doing my best and trying to have fun. I'm learning alot in all this trial and ERROR. Accent on the error.

 louieb.../dev/hda7 was there before I re-did everything. You see what I'm working with now.

Herman...I will definitely be reading your edits tonight. I will certainly be updating you guys on my progress if you don't mind.

Thank you all again for your help.

Regards,
fewjr

---

### Post by fewjr on 2008-10-17
**[COLOR="Red"]EDIT[/COLOR]**

I just figured out how to boot from Ubuntu's recovery & memtest  kernels. When I select Ubuntu from Mandriva's Grub menu I just need to hit Esc to list Ubuntu's Grub menu....simple, like me...LOL. Nice to know it works as is anyway=D>.

---

### Post by Herman on 2008-10-17
> When I select Ubuntu from Mandriva's Grub menu I just need to hit Esc to list Ubuntu's Grub menu....:) Probably the reason for Ubuntu's GRUB menu not showing up automatically for you is because Ubuntu detected it was the only operating system at the time it was installed.
That makes it set up the GRUB menu not to show, for faster booting. (If it's the only operating system, you probably won't need the menu).

To see your GRUB menu, there's a command in your /boot/grub/menu.lst file, namely the 'hiddenmenu' command.
If you want to see your GRUB menu each time you boot Ubuntu, you need to open your /boot/grub/menu.lst file in Ubuntu and place a 'hash mark' in front of it to make your GRUB ignore that command. (And not hide the menu). A hash mark looks like this: # 

See this link for more details,  [hiddenmenu]("http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu"). - show or hide your GRUB menu on boot-up.

So, you need to boot Ubuntu, open a terminal and open your /boot/grub/menu.lst with the following command,
```
gksudo gedit /boot/grub/menu.lst
```And then you can edit your menu.lst file which controls your GRUB menu.

> So I am doing my best and trying to have fun. I'm learning alot in all this trial and ERROR. Accent on the error.:) That's how I learned, (and I'm still learning too, it never ends). :)

> Herman...I will definitely be reading your edits tonight. I will certainly be updating you guys on my progress if you don't mind.Cool!  You will learn quickly, I can tell, you have the right attitude. :)
Yes, if and when it's convenient for you, updates on your progress will be welcomed. Don't be shy to ask any questions. 

Regards, Herman :)

---

### Post by louieb on 2008-10-17
> **fewjr said:**
> I just figured out how to boot from Ubuntu's recovery & memtest  kernels...=D>.

:) Cool.

> &#8220;Never be afraid to try something new. Remember, amateurs built the ark. Professionals built the Titanic.&#8221; -Harry S Truman

---

### Post by Herman on 2008-10-17
Originally posted by louieb
> “Never be afraid to try something new. Remember, amateurs built the ark. Professionals built the Titanic.” -Harry S Truman 			 		:lolflag: Very true! I like that! :)

---

### Post by fewjr on 2008-10-21
Herman,
     Just to update you a little. I'm at work quite a bit lately, but I understand the GRUB partition method a bit better. Especially since you edited your page. I'm getting ready to give it a try. My wife's Vista computer started to take a dump, and I have been working on it. I did change Ubuntu's menu.lst to time out at 10 sec and #ed out hiddenmenu. It works like a charm. I still want to try this other method, so here goes. I'll be back to let you know what happens.

Buddy/fewjr

---

### Post by fewjr on 2008-10-21
Herman,
     Well...it halfway works so far. The GRUB partitiontakes over like MBR tells it to. I set my configfile entries so that Ubuntu is first on the list. Mandriva second. It boots into Ubuntu fine, but not so with mandriva. I get this message:

```
error 23: Error while parcing number
```

So I have to figure that out. Also, e2label doesn't work for me. If I go into Places>computer within Ubuntu It still labels Ubuntu as 'Filesystem' and the Mandriva partition as 'Disk'. So I'm not sure where I went wrong there. It seemed very easy when I read your tut.

---

### Post by Herman on 2008-10-21
Error 23 could be caused by something simple like a spelling mistake in one of your commands in your GRUB menu or a syntax error.
Typing a letter 'O' where the should be a number '0' (Zero), is one way to make GRUB Error 23 appear. (where you have 'root (hd0) for example, that's like '(hd zero)'.
I don't know why your file system labels wouldn't be working unless I have more clues, but I have some good news for you about that. Intrepid Ibex, the next release of Ubuntu, (still a few days away), includes the ability to add or edit file system labels in Gnome Partition Editor, (in the GUI). I think GParted Live CD has had that ability for a while. 
If you have too much trouble with the command line you could always fall back on one of those ways to get your file system labels set.
Take a look at the first five illustrations in my [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm")  if you want to see what I mean.
Regards, Herman :)

---

### Post by fewjr on 2008-10-21
Yeah....I figured it might be something simple. I'll look at it tonight.

---

### Post by fewjr on 2008-10-22
Okay...that was it exactly, an o instead of a 0. It boots into Mandriva just like it is supposed to now. Nice huh :). There is some other questions though, sorry. If I am in Ubuntu or Mandriva and do 'gksudo gedit /GRUB/boot/grub/menu.lst' or 'kwrite /GRUB/boot/grub/menu.lst' respectively I can not see anything in the text editor. I do not get any errors just a blank page in gedit or kwrite. I have tried mounting the GRUB partition before doing it, but no go. The same goes for trying to open the two distros menu.lst files. If I navigate to the directory, the file is there and I can double click it and read it, and like I said GRUB partition works great. Just wondering why I cannot bring it up with those commands to edit it. The way I did get to fix my error in the configfile was to run the command 'gksudo gedit /GRUB/boot/grub/menu.lst'. When it came up empty, I opened /GRUB/boot/grub/menu.lst from within gedit and there it was (I was root because I opened gedit with sudo). But why doesn't it come up just from the terminal command. I hope I'm being clear. I also got alot of errors when I opened kwrite from the Konsole in Mandriva. They don't have anything to do with this thread though, so I won't even go there. I don't like the feel of Mandriva-KDE anyway. I like Gnome better, so Suse is going on instead and something else.  What do you like? Thanks again for all your help. I love your website. I am working on dual-booting with two drives- (windowsXP, linux, linux, linux). Its a brand new computer that Ubuntu does NOT like. It has an nVidia geforce8200 chipset. Ubuntu needs pci=nomsi to run livecd and install. Also has sata drives. I had to set bios to AHCI instead of IDE to get it to install. Funny thing is I partitioned drives over again and installed WinXP on it. I had to set bios back to IDE to get it to install. WinXP has issues with AHCI. When does it ever end!!!!!:-({|=

Buddy/fewjr

---

### Post by Herman on 2008-10-22
> If I am in Ubuntu or Mandriva and do 'gksudo gedit /GRUB/boot/grub/menu.lst' or 'kwrite /GRUB/boot/grub/menu.lst' respectively I can not see anything in the text editor.:) Yup, well that's because there is no such file as '/GRUB/boot/grub/menu.lst'.
There's a /boot/grub/menu.lst, but there;s no file called '/GRUB/boot/grub/menu.lst', so Gedit thinks you're wanting to make a brand new empty file.
You can open the Gedit text editor with any file name you care to make up and it will save that file as whatever file-name you opened it as. :)

So if I enter 'gedit mushroom', in my terminal, it'll open an empty file and name it 'mushroom, so as soon as I save the file (even if it's empty), I'll have a text file named 'mushroom'.

The best thing I can tell you to help you learn Linux easier is to try using a feature called 'tab completion'.
'Tab completion' is accomplished by typing the beginning of something in your terminal and then pressing your tab key. Linux will try to guess what it is you are trying to type and will automatically complete it for you or show you a list of suggestions.

For example, I might type: 'gksudo gedit /' in my terminal and press tab key. Nothing will happen, but if I press it again it will show me a list of folders in my / directory, so I can see what's there and pick one.
```
herman@amd64-intrepid:~$ gksudo gedit /
bin/            dev/            initrd/         lib/            media/          proc/           srv/            usr/            vmlinuz.old     
boot/           etc/            initrd.img      lib64/          mnt/            root/           sys/            var/            
cdrom/          home/           initrd.img.old  lost+found/     opt/            sbin/           tmp/            vmlinuz
```Okay, now I can see there's a directory there called /boot, all I need to type is an additional 'bo' -and press tab, and the name 'boot/' will be automatically completed for me.

Then I type 'gr' - and press tab again and the word 'grub/' will be completed automatically.

Then I type 'me' -and the name 'menu.lst' will be filled in for me.

It's a good idea to use 'tab completion' almost all the time when we're using the Linux terminal, because it not only saves a lot of typing, it also saves spelling mistakes and ordinary errors, and it's a good way to 'take a look around and see where we're going' in the terminal too. :)

So anyway, (after all that), it's gksudo gedit /boot/grub/menu.lst, not '/GRUB/boot/grub/menu.lst',
```
gksudo gedit /boot/grub/menu.lst
```Another thing you can do is copy commands from websites you trust and paste them into your terminal and run them, but you should only do that is you know what the command is for, (what it is supposed to do).
Opening your menu.lst file is quite a safe thing to do.
If you ever do make a mistake editing your /boot/grub/menu.lst file you will still be able to boot it you have a Super Grub Disk or any GRUB CD or floppy disk or USB. 
> I like Gnome better, so Suse is going on instead and something else. 
What do you like?  Personally, I prefer the Gnome desktop, that's my favorite too, by a long way.
Every now and again I enjoy playing with other desktops like KDE, XFCE, IceWM and others, but to use full time I'm a Gnome user.

Thanks, I'm glad you like my website. It always makes me happy if I can use it to help other people to get more use and fun out of Ubuntu. 

I don't have any nVidia cards myself, I'm glad you got it working somehow, also the AHCI/IDE thing sounds ood, but yes, that's what things are like sometimes with computers. Sometimes we learn why later and then it makes sense, but often we just have to accept strange things and learn to live with them. :)
> When does it ever end!!!!!:-({|= The fun never ends, I'm still learning new things every day, and things I thought I knew keep going out of date too. And sometimes things I think I know turn out to be wrong even! :lolflag:
The only thing to do is laugh about it and keep on having fun, trying new ideas and learning more.

Best Regards,
Herman :)

---

### Post by fewjr on 2008-10-23
Hi Herman,
     > Yup, well that's because there is no such file as '/GRUB/boot/grub/menu.lst'.
There's a /boot/grub/menu.lst, but there;s no file called '/GRUB/boot/grub/menu.lst'

I get ya I think except for if I issue the command 'gksudo gedit /boot/grub/menu.lst', wouldn't that bring up Ubuntu's menu.lst file not the one in the GRUB partition? If I wanted to bring up menu.lst from GRUB partition would'nt I have to take the path /media/GRUB/boot/grub/menu.lst? I left out /media in my last post, but I meant that. 
     I hope you don't mind me asking all these questions. I have read about tab completion. I will start using it now that you have straightened me out on it. I really don't have that much time in all this. Still in the setting up stage. And whats the difference between sudo and gksudo anyway? I think I read something about it awhile back, but it didn't stick. Well I have this Pentium3 dual booting the way I wanted it, so we'll have to see how the newer computer fairs here soon when I get everything setup. That one will have windowsXP and 2 hard drives as I mentioned earlier. Hey you know, some of my problem might be age setting in or something. I am 51, have 5 daughters and work swing shift. Something has got to break...#-o. Have a good one Mr Herman. Talk at ya later, gotta get back to work.

                   Best Regards to you too!
                        Buddy/fewjr

---

### Post by Herman on 2008-10-23
> 'gksudo gedit /boot/grub/menu.lst', wouldn't that bring up Ubuntu's menu.lst file not the one in the GRUB partition? If I wanted to bring up menu.lst from GRUB partition would'nt I have to take the path /media/GRUB/boot/grub/menu.lst? I left out /media in my last post, but I meant that.:) Oh, yeah, you're right. Sorry about that, my bad, I didn't realize you meanrt and implied '/media/' and just thought you wanted you normal GRUB menu. 
> I hope you don't mind me asking all these questions. I don't mind.
> And whats the difference between sudo and gksudo anyway? I think I read something about it awhile back, but it didn't stick.
There's an article about it by aysiu, here, [Graphical sudo]("http://www.psychocats.net/ubuntu/graphicalsudo").
> Hey you know, some of my problem might be age setting in or something. I am 51, have 5 daughters and work swing shift. Something has got to break...#-o
Hmmm, well I'm a 48 year old ex trucker but now concrete worker and it took me some time to figure all thsi stuff out too. It's not as if there's a handy university out here in the Australian Outback where we can go to learn Linux or computer programming, so I had to figure most things out myself by experimenting and researching, (mainly right here in Ubuntu Web Forums). It's a great hobby and I have a lot of fun with it. Just 'hang in there'. :)

---

### Post by fewjr on 2008-10-24
I read the link on gksudo....Thanks, and I'm hangin in. You take it easy with the concrete!

---

### Post by fewjr on 2008-10-24
Just a quick update....I just installed Ubuntu on my new computer with WinXP. this is the computer with the Geforce 8200 chipset. It worked just like you explained on your site. I will probably change it around so I am using both drives and a GRUB partition too later. I have to get to sleep for a bit.

---

### Post by fewjr on 2008-11-03
I know I set this as solved, but I was wondering.....I have WinXP And Hardy duel booting using the GRUB partition method. I have a couple more partitions ready for other distros. When I install another version of Linux, say Ibex maybe, I would use manual and chose the partition I want and set it to / right? And when it ask if I want to install grub should I or not, and if I should....where should it go? I tried to install Ibex to a 100GB partition, but of course Ibex is seriously broken in the early stages. Now that I have hardy & XP working so well I didn't want to mess it up. So I just thought I'd check with you. Herman if your still subscribing to this thread, I would of sent you a message, but I don't have 75 post quite yet. So I hope you see this.

fewjr

---

### Post by Herman on 2008-11-03
:) If you install GRUB for the new operating system to the first sector of the operating system's own partition you can chainload it from your main GRUB menu.

To do that, make sure you're paying attention when you get to step 7 of 7 in the Live CD installation process and click the 'advanced' button.
Click the arrow to the right of the feild for where to install a boot loader and you'll be given a drop-down menu. You can select a MBR or a partition from that menu.

When your computer reboots after the installation has finished, it will just reboot into your old operating system.
When your old operating system has booted up, you can edit your main GRUB menu to include a 'chainlaoder' boot stanza so your existing GRUB will chainload your new GRUB at the boot sector you installed the new GRUB in.
Here's a link that should help you, [Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems").
If you still have trouible, let me know and I'll try to explain better.
Have fun!

Regards, Herman :)

---

### Post by fewjr on 2008-11-03
Hmmm.....I thought I was using configfile entries. Did you mean configfile and not chainload? So your saying I was doing it right installing grub during Ibex install to the 1st sector of its / partition? Because thats what I did. I couldn't check to see if it worked because Ibex has issues right now and wouldn't install right. I'll try openSUSe next. Well this is where I may need a little more clarification. I have read that section of your site a few times and I understand it. I do want all the distros to be able to update right, so using the dedicated GRUB partition I should install grub with each distro I install to its / partition and update my menu.lst in GRUB partition after. I thought thats what I was supposed to do. All my linuxes will update automacically with this setup?
      So since Ubuntu gives you the option to not install grub at all under advanced....when would you not want to install grub? What situation would that apply? 

Buddy/fewjr

---

### Post by fewjr on 2008-11-03
Man Herman...I read it again. Your site says: 

> We can also chainload another Linux with its own GRUB installed to the first sector of its / (root) partition.  The other Ubuntu or other distro you will be booting will use it's own GRUB or LiLo menu. Since it's own menu is kept up to date by the operating system it belongs to, it should always be up to date.
The chainloader command hands over control to the other other operating system's GRUB stage2 file as well, so it does a bit more than the configfile command.


I guess I need to open my eyes wider. So this is the way you do it if you want them to update properly (automagically)?

---

### Post by Herman on 2008-11-03
:) , yes, you can use either command, chainloader or configfile.

The configfile command is often quicker and a little bit easier, because you don't need to install GRUB somewhere first, like to the first sector of a partition, or to another (non-first) hard disk's MBR.

The chainloader command can be more work to set up but since you're installing anyway, it's no extra effort to direct the installer to install GRUB where you specify.
The chainloader command is slightly more useful, because it can boot other bootloaders like LiLo or Windows boot loaders. 

The configfile doesn't boot the other system's GRUB, it just uses it's /boot/grub/menu.lst for directions. 

In your case, this time you can use either one, whichever your prefer.
> so using the dedicated GRUB partition I should install grub with each distro I install to its / partition and update my menu.lst in GRUB partition after. I thought thats what I was supposed to do. All my linuxes will update automacically with this setup?
 :) Yeah, that's right, that's the way to do it, exactly! 
You add a chainloader or a configfile boot stanza to your dedicated GRUB partition's GRUB (your main GRUB menu).

Then if you used the configfile command your main GRUB, (from your dedicated GRUB partition), will refer to the menu.lst of the operating system you're going to boot up and use the information it contains to boot it with, (or you can select to boot something else from that second menu too if you want).
If you used the chainloader command, then GRUB from your dedicated GRUB partition hands over control to GRUB in the operating system you're booting,  LiLo or Syslinux or NTLDR or whatever boot loader you installed there in the other operating system.
With either command, you'll be booting the other operating system by it's own boot loader and/or configuration file, so if the other operating system's menu.lst has been automatically updated with new information such as a new kernel, you don't have do do any work and you'll be automaticallt boot ing it by it's most up to date kernel every time. :)
> So since Ubuntu gives you the option to not install grub at all under advanced....when would you not want to install grub? What situation would that apply? I don't know, it would be rare  to not want to install a boot loader at all. Even if someone didn't like GRUB, they could still install it and then install some other boot loader or boot manager right away afterwards. 
We can have Grub and LiLo both at the same time, and GAG too if we want, all in the same /boot directory, there's no conflict. One can be installed to a MBR and another to a partition's first sector if we want.
Boot loaders don't take up very much hard disk space either, so I don't know why anyone would want to install without any boot loader at all. Maybe for some special experimental purposes?

Regards, Herman :)

---

### Post by fewjr on 2008-11-04
Hi Herman,
 
> Then if you used the configfile command your main GRUB, (from your dedicated GRUB partition), will refer to the menu.lst of the operating system you're going to boot up and use the information it contains to boot it with, (or you can select to boot something else from that second menu too if you want).
If you used the chainloader command, then GRUB from your dedicated GRUB partition hands over control to GRUB in the operating system you're booting, LiLo or Syslinux or NTLDR or whatever boot loader you installed there in the other operating system.
With either command, you'll be booting the other operating system by it's own boot loader and/or configuration file, so if the other operating system's menu.lst has been automatically updated with new information such as a new kernel, you don't have do do any work and you'll be automaticallt boot ing it by it's most up to date kernel every time. 


     Okay...but I don't see what the difference between these two methods are. They both hand over control to that operating systems menu.lst file. I'm sorry if I'm going in circles. I guess I'm trying to get this stuff under my hood between all my working hours and sleep time. I'm enjoying it though.

> With either command, you'll be booting the other operating system by it's own boot loader and/or configuration file

 "it,s own boot loader and/or configuration file" I think this is what is not sinking in. :oops:. During install of another operating system, you would have to install the boot loader somewhere or there would be no config files to direct right? The boot loader is the stage1 stuff? I think I'm starting to sound like a moron..LOL. I better read some more till I get it all up in my head for good.

Thanks Herman

---

### Post by Herman on 2008-11-04
:), Hmmm, I think it's my fault for not explaining things well enough.

Okay, your computer is booting right?
The first thing that happens is, the BIOS looks around for a bootable device, like a CD or a floppy disk maybe, or the MBR of the first hard disk.
If the stage1 file of GRUB in installed to the MBR of your first hard disk, your MBR  'points to' the stage2 file of GRUB in your dedicated GRUB partition. 
The Stage2 file is the main part of GRUB, it's by far the largest, and it's the one that does all the work.
Your Stage2 looks at your /boot/grub/menu.lst and shows you your GRUB menu, and when you select an operating system to boot, Stage2 will try to boot it.

If your operating system entry is a direct kernel boot type of entry, Stage2  of the GRUB you are using will try to boot the operating system directly by loading the kernel into the RAM.

If the operating system entry, (or boot stanza), is a 'configfile' type of boot entry, the Stage2 from the GRUB you are using will look at the /boot/grub/menu.lst of the other operating system, and it will show that GRUB menu to you and read the commands from that menu.lst file and use those to boot the operating system you selected.  (The same stage2 file is still doing the work).

If the the operating system entry is a chainloader command, then the first GRUB, (in your dedicated GRUB partition), will boot the operating system's GRUB by booting it at the boot sector, (first sector of the partition).
When that happens, the stage2 file from the first GRUB hands over control to the stage 2 file of GRUB in the operating system, or if the operating system has some other boot loader then control is handed over to that one. Then you will see the menu from whatever other boot loader you have in the operating system you want to boot. It could even be LiLo or Syslinux or GAG Boot Manager, or NTLDR or something else.  :)

Most of the time we can use whichever command we like. The configfile command is the quickest and easiest. The chainloader command is more versatile, since it can boot other boot loaders or other versions of GRUB. The disadvantage of using the chainlaoder command is just that the other boot loader needs to be installed to a MBR or boot sector before chainloading will work. (Or more accurately, the stage1 file of the other boot loader needs to be in the MBR or boot sector.

If you're still unclear, don't be shy to ask me more questions and I'll try to think of better answers. 
Things will also become clearer with practice and especailly  if you try a few experiments. Grub can be quite interesting and fun to play with. :)

---

### Post by fewjr on 2008-11-05
:cool:.....Are you sure you work in concrete! That was a very well put explanation. I do see the difference now. I have a couple days off after tonight. Hopefully I'll get a chance to play with it a little. Thanks a heap for all the tutoring:biggrin:. I know I should be doing more of the research on my own, but I have been finding it hard to find time to do all the searching. You've been great. Thanks alot Herman. I'm sure I'll find something else to confuse me. Glad to know you don't mind the questions.

fewjr

---

### Post by fewjr on 2008-11-05
Okay Herman.....I've been looking around and I am still wondering what situation would cause any distro you have installed to not update automagically? So far I've gotten openSUSE to install. It works fine and so does Mandriva which I don't like much (KDE). I tried to install MintLinux and it gets to the step where you assign partitions in the partition editor. Weird thing is it doesn't show any drives or partitions to edit. Mepis just goes to a black screen after it boots the cd. I'll md5sum the disc. The isos were fine.

---

### Post by fewjr on 2008-11-05
Well I've done something wrong.I can't get into Ubuntu now. I ran gparted-livecd and was going to make a screenshot of my partition setup to show you and now I get "error 17 cannot mount the partition". I think I need to make a grub disk, but this computer doesn't have a floppy drive. The terminal in gparted-live doesn't know grub commands. :confused:

---

### Post by Herman on 2008-11-06
You should try booting your GParted LiveCD again and run a file system check in your Ubuntu partition.
A file system check has been able to cure GRUB Error 17 sometimes.

There are other problems that can cause GRUB Error 17 as well, one of them is your partition number for Ubuntu might have been changed. I don't know how that happens, but it does sometimes. If that's what happened, you might just need to edit your /boot/grub/menu.lst file with a different partition number to fix it.

Here's my list of things that can cause GRUB Error 17, [Grub error 17]("http://users.bigpond.net.au/hermanzone/p15.htm#17").
The information in that link is designed to try to help you solve the problem, but if you still need help then just ask. Please post a copy of 'sudo fdisk -lu' and the bottom half of the /boot/grub/menu.lst file if you need specific help. (Probably your Ubuntu Live CD would be the best to use for getting those.
I or anyone else who is interested will help you if necessary. :)

Regards, Herman :)

---

### Post by fewjr on 2008-11-06
Here you go Herman,
     
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e557f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   124310969    62155453+   7  HPFS/NTFS
/dev/sda2       124310970   976768064   426228547+   5  Extended
/dev/sda5       124311033   334023479   104856223+  83  Linux
/dev/sda6       334023543   438879734    52428096   83  Linux
/dev/sda7       438879798   439088579      104391   83  Linux
/dev/sda8       439088643   443281544     2096451   82  Linux swap / Solaris
/dev/sda9       443281608   548137799    52428096   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000487cb

   Device Boot      Start         End      Blocks   Id  System
ubuntu@ubuntu:~$ 

     All that looks right to me. I ran the e2fsck commands from your site. That went well too it looks like. I wanted to send a screenshot out of gparted-livecd, but it would'nt work for me. I don't understand where it goes when it saves it. It says in /root, but what root? I'm still reading.

---

### Post by fewjr on 2008-11-06
Well what do you know, it boots again. Thanks again. I want to figure out this screenshot thing. I'll post it if I get it.

---

### Post by fewjr on 2008-11-07
Do you have anything on your website about running md5sum on cd? For some reason it seems to hang in the terminal. I believe I have done it before and it worked. I tried :

```
cd /cdrom
md5sum -c
```

I also tried to cd to /media/cdrom, /media/cdrom0. The terminal is still sitting there with a blinking cursor....its been 2 hours like that. I've read a bunch of howtos. I want to check my linuxmint and mepis cds, because they won't work right. Right now I'm running md5sum on a good copy of ubuntu 8.04 that I installed with just to figure out how to check it manually. But its stuck...or I am.
     fewjr

---

### Post by Herman on 2008-11-08
I don't have anything in my website about how to check the CD with an md5sum, just how to check the downloaded .iso file, [Checking the integrity of your .iso in Ubuntu]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Checking_the_.iso")

The 'Desktop' and 'Alternate' Ubuntu installation CDs have an option at the boot menu called 'Check CD for Defects' instead, which I think runs an md5sum test on the CD itself somehow. If your CD passes that, it should be okay.
I don't know whether other Linux distros have anything like that or not.

I have had problems myself a few times with poor quality CDs and DVDs, make sure you buy a good brand and not just the cheapest CDs and DVDs.
I have also run into problems with dirt or scratches on optical media, make sure you always handle your discs properly, pick them up by the edges or by the hole in the middle so you won't get fingerprints on them, and always put them away in a CD case, never put them down on a table or a shelf. Even invisible dirt can cause problems.
I have also had to clean out my CD/DVD drives and wipe the optical lense with a cotton bud (Qtip) dipped in metho (denatured alcohol). I wouldn't recommend anyone else do that unless your really need to though, try running the 'Check CD ofr Defects' test in a different computer first, to see if it's the CD/DVD drive or the media that needs cleaning/ or replacing.

---

### Post by fewjr on 2008-11-09
I know about checking Ubuntu disks, but it is the other distros I would like to check. In any case I thought I would post what the Pentium 3 machine menu.lst files look like for anyone who may read this thread. This machine does not have Windows installed like the nVidia 8200 chipset machine I have been working on at the same time. This one has Ubuntu Hardy Heron, Mandriva, LinuxMint and Ubuntu Intrepid Ibex. I started out installing Hardy first. Then I made the GRUB partition. I used gparted-livecd to make a few more partitions for the other OSes. With each OS that was installed I chose manual and set as  root, installing grub to that OSes first sector. Each install populated its menu.lst with all the other OSes entries. So by the time I installed Ibex on the last partition, it had entries to all the boot kernels on the hard drive. So Hardy had its own entries, Mandriva had its own plus Hardy's, LinuxMint had its own plus Mandriva's and Hardy's and Ibex had all entries that came before it plus its own. That seemed a little bit crowded to me so I cleaned up each distros menu.lst file to only show their own entries. That made things look a little tidier to me. The only problem I saw with doing that was that Ibex will not boot as of yet and all those other entries had been taken out so I could'nt loop back to any of the other distros to boot unless I rebooted totally. So things have worked out and I learned alot from this. I'm not sure why Ibex won't boot yet. I read something earlier about Ibex having something different as far as the way the kernel is booted. I get a "grub error 15" when I try to boot it. And if I try to boot it with SGD I get an "error 13: Invalid or unsupported executable format". The livecd runs Ibex fine and I had no problems installing it. It just won't boot. Here are the menu.lst files from the P3 machine:

[COLOR="Red"]GRUB partition:[/COLOR]
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3b4b3553-7b3c-4063-b938-7e6d3590928c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04 Hardy Heron
configfile      (hd0,0)/boot/grub/menu.lst

title		Mandriva 2008-spring-KDE
configfile      (hd0,4)/boot/grub/menu.lst

title           LinuxMint 5
configfile      (hd0,5)/boot/grub/menu.lst

title           Ubuntu 8.10 Intrepid Ibex
configfile      (hd0,7)/boot/grub/menu.lst
### END DEBIAN AUTOMAGIC KERNELS LIST

```

[COLOR="red"]Ubuntu Hardy:[/COLOR]```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
  color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3b4b3553-7b3c-4063-b938-7e6d3590928c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3b4b3553-7b3c-4063-b938-7e6d3590928c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3b4b3553-7b3c-4063-b938-7e6d3590928c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

[COLOR="red"]Mandriva:[/COLOR]```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd0,4)/boot/gfxmenu
default 0

title linux
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=760acc10-1f49-45e0-ba6f-9885b59ab482  resume=/dev/hda2 splash=silent vga=788
initrd (hd0,4)/boot/initrd.img

title linux-nonfb
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=760acc10-1f49-45e0-ba6f-9885b59ab482  resume=/dev/hda2
initrd (hd0,4)/boot/initrd.img

title failsafe
kernel (hd0,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=760acc10-1f49-45e0-ba6f-9885b59ab482  failsafe
initrd (hd0,4)/boot/initrd.img



```

[COLOR="red"]LinuxMint:[/COLOR]
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

gfxmenu=/etc/grub/message.elyssa

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Linux Mint, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST



```

[COLOR="red"]Ubuntu Ibex:[/COLOR]```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
 color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9557d1b8-983d-4008-85a3-d8cd31f6d253

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



```

Thanks again,
fewjr

---

### Post by fewjr on 2008-11-09
I think my Ibex boot problem has something to do with this UUID thing. this is an entry from Hardy:

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3b4b3553-7b3c-4063-b938-7e6d3590928c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

This is an entry from Ibex:

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

```

Note that Ibex doesn't use (hd0,x) rather it uses UUID. Thats what I thought I read something about yesterday. Any ideas on a work around? I think I'm going to change the Ibex entries to the root (hd0,x) method instead of UUID and see if it works. I will be sure to save a copy of the menu.lst file though. Here goes nothing...update soon.:biggrin: This is wild!

---

### Post by confused57 on 2008-11-09
Hi fewjr,
   Herman is the best around for solving & explaining boot problems, as well as any other problems or questions you may have concerning Linux.

I installed Ibex & couldn't get the configfile method to work, however, chainloader method worked fine.

---

### Post by fewjr on 2008-11-09
ahh...yeah, I can see how that would do it. Thanks.

---

### Post by Herman on 2008-11-09
> Note that Ibex doesn't use (hd0,x) rather it uses UUID. Thats what I thought I read something about yesterday. Any ideas on a work around? I think I'm going to change the Ibex entries to the root (hd0,x) method instead of UUID and see if it works. I will be sure to save a copy of the menu.lst file though. Here goes nothing...update soon.:biggrin: This is wild! My Intrepid Ibex doesn't have that new UUID line for the root yet. I just ran 'sudo apt-get update' and 'sudo apt-get upgrade'.
I don't know about that yet, it might be something new that I haven't heard of yet..
I guess you should be able to revert back to the normal style of Ubuntu booting stanza for the time being.
I wonder if anyone else has seen a booting stanza like that? :D

---

### Post by confused57 on 2008-11-09
> **Herman said:**
> My Intrepid Ibex doesn't have that new UUID line for the root yet. I just ran 'sudo apt-get update' and 'sudo apt-get upgrade'.
I don't know about that yet, it might be something new that I haven't heard of yet..
I guess you should be able to revert back to the normal style of Ubuntu booting stanza for the time being.
I wonder if anyone else has seen a booting stanza like that? :D
Hello Herman,
   How's it going?  My new install of Ibex also has a UUID in place of (hdx,y), which must be why the configfile method didn't work? 

Jim

---

### Post by fewjr on 2008-11-09
Yeah guys.....it works if you switch it back to root (hd0,x). I just finished and Ibex boots. Here is the before and after:

[COLOR="Red"]Before[/COLOR]
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro quiet splash 
initrd	        /boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel	        /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro  single
initrd	        /boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel	        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

[COLOR="red"]After[/COLOR]
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,7)
kernel	        /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro quiet splash 
initrd	        /boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd0,7)
kernel	        /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro  single
initrd	        /boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root            (hd0,7)
kernel	        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



```

But one thing I'm wondering, will it update properly like we were talking about before Herman? Otherwise I may need to do chainloading like confused57. I'm very curious as to why you didn't have the UUID entries as we did. I did read in the sticky under installation and upgrade something about this. So I'm sure its been seen by others. This P3 hasn't been connected to the internet yet, because I've been sneaking a bit of work on it here at work where I don't have internet access for it. I'm typing from a computer in another building here at work. Maybe yours downloaded some updates and fixed this before you noticed it. But if your duel-booting you should have had the problem we had unless Ibex was the first OS installed, if that would have mattered. Or maybe you had it installed alone on your computer. Will it update automagically like I have it now you think guys? Thanks for jumping in confused57. Talk later fellas:D

---

### Post by deltaprime on 2008-11-09
incase anyone cared its called dual not duel.....

---

### Post by confused57 on 2008-11-09
> **fewjr said:**
> Yeah guys.....it works if you switch it back to root (hd0,x). I just finished and Ibex boots. Here is the before and after:

[COLOR="Red"]Before[/COLOR]
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro quiet splash 
initrd	        /boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel	        /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro  single
initrd	        /boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel	        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

[COLOR="red"]After[/COLOR]
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,7)
kernel	        /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro quiet splash 
initrd	        /boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root            (hd0,7)
kernel	        /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro  single
initrd	        /boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root            (hd0,7)
kernel	        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



```

But one thing I'm wondering, will it update properly like we were talking about before Herman? Otherwise I may need to do chainloading like confused57. I'm very curious as to why you didn't have the UUID entries as we did. I did read in the sticky under installation and upgrade something about this. So I'm sure its been seen by others. This P3 hasn't been connected to the internet yet, because I've been sneaking a bit of work on it here at work where I don't have internet access for it. I'm typing from a computer in another building here at work. Maybe yours downloaded some updates and fixed this before you noticed it. But if your duel-booting you should have had the problem we had unless Ibex was the first OS installed, if that would have mattered. Or maybe you had it installed alone on your computer. Will it update automagically like I have it now you think guys? Thanks for jumping in confused57. Talk later fellas:D

Thanks for the update, good info to know...I believe you'll need to update the line with groot to (hd0,7):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)
As you can see, I'm constantly referring to Herman's site for advice...you might want to wait & see what he thinks.

---

### Post by fewjr on 2008-11-09
Yeah....I've become a fan. Herman has made this more fun for me for some reason. Anyway, older versions of grub cannot read the 256-inode ext3 file system used by Intrepid whatever that means.  I read it here on another thread I saw: [http://ubuntuforums.org/showthread.php?t=945754](http://ubuntuforums.org/showthread.php?t=945754), page2> #14. Apparently what I did works fine for booting it though. So duel dual...nope don't care I guess=;

---

### Post by meierfra. on 2008-11-09
[QUOTE=herman]My Intrepid Ibex doesn't have that new UUID line for the root yet. I just ran 'sudo apt-get update' and 'sudo apt-get upgrade'.[/QUOTE]

Rename your Intrepid menu.lst and run "sudo update-grub" to create a new menu.lst. That should give you "UUID=..." instead of "root (hdX,Y). Maybe you also have to run "grub-install" to put the new stage2 files in use.


[QUOTE=confused57]which must be why the configfile method didn't work? [/QUOTE]

Yes.  Only the intrepid stage 2 files can handle UUID's. If you want  to use "UUID" and the configfile method, copy the stage2 files from the Intrepid partition to the grub partition. (That should be enough, if not copy all the stage files to the grub partition and reinstall grub)

I really like the new uuid format. It means that one can delete and move partitions without having to reinstall grub and edit menu.lst. (This works as long as the grub partition stays in the same place)

---

### Post by Herman on 2008-11-09
> Hello Herman,
 How's it going? My new install of Ibex also has a UUID in place of (hdx,y), which must be why the configfile method didn't work?:) Hello confused57,  thank you for your help here, yes that does seem to be the problem all right, I ran an experiment which seems to prove it.


> Rename your Intrepid menu.lst and run "sudo update-grub" to create a new menu.lst. That should give you "UUID=..." instead of "root (hdX,Y).:) Thank you, meierfra, that worked.


> I think my Ibex boot problem has something to do with this UUID thing. this is an entry from Hardy:

     Code:
     title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=3b4b3553-7b3c-4063-b938-7e6d3590928c ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet 
This is an entry from Ibex:

     Code:
     title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        9557d1b8-983d-4008-85a3-d8cd31f6d253
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=9557d1b8-983d-4008-85a3-d8cd31f6d253 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic 
Note that Ibex doesn't use (hd0,x) rather it uses UUID. Thats what I thought I read something about yesterday. Any ideas on a work around? I think I'm going to change the Ibex entries to the root (hd0,x) method instead of UUID and see if it works. I will be sure to save a copy of the menu.lst file though. Here goes nothing...update soon.:biggrin: This is wild!     
:) Thank you too, fewjr, this is the first I have known of this particular booting problem or of UUID numbers being used in place of GRUB's 'root' command.

Surprisingly, after updating my Intrepid's GRUB to the new 'UUID for root' menu.lst, my dedicated GRUB was still able to boot it with the configfile command without any problem.
Maybe my dedicated GRUB is already a fairly recent copy of GRUB from Intrepid, I can't remember for sure, but it could be. I think so.
Then I chainloaded my Hardy Heron GRUB from my dedicted GRUB and then tried the configfile command to boot Intrepid, and - sure enough - Error 15: File not found!
Chainloading worked fine, as expected.
So, we can't use the configfile command from the older GRUB for booting via the newest GRUB's menu.lst, we will need to chainload it instead.
Thank you all, I will need to get busy and update my GRUB page and possibly some other places in my website in the light of this new feature.

I can hardly wait to try it out with some more experiments too, and see how well it works for booting with multiple hard drives and USB flash memories and so on. I expect to find that this (UUID for root idea), will be a good and useful feature for GRUB!

Regards, Herman  :)

---

### Post by meierfra. on 2008-11-09
[QUOTE=fewjr]Anyway, older versions of grub cannot read the 256-inode ext3 file system used by Intrepid whatever that means. ... Apparently what I did works fine for booting it though. [/QUOTE]

Hardy's   Grub can already handle the 256 inodes, but not the UUID's.
Only any version before Hardy cannot handle the 256 inodes. 
To make matters more complicated:  If one upgrades from one Ubuntu version to another, the  stage files in /boot/grub are not being updated. So Hardy users which upgraded from Gutsy can have problems with 256 inode file systems.

---

### Post by fewjr on 2008-11-09
Thanks Guys,
     So I think I'm the one that is still wrapping his mind around this. You all have way more experience with it. So when I made my Dedicated GRUB partition and brought in the grub files from Hardy originally and edited with configfiles I was golden, but now with Ibex being installed I need to do that step over using Ibex's grub files instead right? Then I need to edit that menu.lst in GRUB partition to chainload Hardy, Mandriva & LinuxMint. Thats what I think your saying.
     I have a question though. If I leave it the way I have it, (edited Ibex's menu.lst with root (hdx,y) instead of UUID entries), what problems will it cause. All OSes boot up fine now, but I'd appreciate it if you could tell me what could go wrong with it this way.
     I'm glad to redo it though, because I haven't gotten a chance to setup chainloading yet. 

Have a good one
fewjr

---

### Post by meierfra. on 2008-11-09
> If I leave it the way I have it, (edited Ibex's menu.lst with root (hdx,y) instead of UUID entries), what problems will it cause.
None. You can leave it as it is.

---

### Post by Thomas Garman on 2010-03-12
I have been thinking about doing the same thing, i.e. dual booting various distros, so the posts here are of great interest to me.  But, the question I have been pondering is this:  why bother?

I have been thinking of putting Mint 8 in a virtualbox under Vista.  I already have Xubuntu in a virtualbox under Vista.  I dual boot Vista Ultimate and Karmic.

Other than a different package handling system, I really don't see the point.  And getting the same software some other way than through Synaptic or Apt-get is not really worth the download time.  So, why would anyone want to use another distro since the kernel is the same and all of the desktops can be customized and basically all the exact same software is available for every linux distro.

---

### Post by Herman on 2010-03-13
:D Well you are right about that. it does seem kind of silly to multi-boot when we can install just about all the same softwares in any Linux distro.

There's not much point in multi-booting between different kinds of desktops either, like Ubuntu, Kubuntu, Xubuntu and so on. We can install more than one desktop at a time in the same operating system with a simple apt-get command, and then it's just a matter of choosing the desktop we want at login time.

For me it does make a little sense to multiple boot, because I like to keep my old Ubuntu operating systems around so I install beside them rather than upgrade or delete them and re-install.
Often I install a test version of Ubuntu which hasn't been released yet and so is still 'unstable', and thus unsuitable for serious use.
In that case I need my regular installation for most of my work and play.
Then when the new version is released I still keep my old versions both for nostalgic purposes and also as a utility system.
Besides that if I'm trying to help somebody with a problem in an older Ubuntu, I might need to go back to it myself to remember what the older Ubuntu was like, so I can give the right advice.
Some older versions had file system UUIDs in /etc/fstab, then file system UUIDs were added to the GRUB boot loader in a copule of increments, then we were given GRUB2, and so on.

My wife multi boots so that is she has some kind of a problem with her Ubuntu and I'm not home she can simply boot the other installation and keep doing whatever she's trying to get done until I come home and fix the problem, it saves a lot of stress.

A journalist or somebody studying to become a journalist or even doing a homework assignment might want to multi boot if they normally use one distro but they want to do an assignment or write an article about a different distro, comparing different package management systems or something. Apart from different package management systems, there are different cultures and different prevailing attitudes in the web forums of various distros. You don't really need to install other distros to find that out though, just go visit their forums.

Others multi boot to satisfy their curiosity or just because they think it will be fun. Some like to learn how to use partition editors and set up their boot loaders as an educational experience too.
It's also possibly a status symbol for some, demonstrating that they have gained enough understanding and mastery over their computers to be capable of setting up and maintaining a sightly more complex arrangement than is really needed by the average Joe User.

It might also be that some Linux users have friends in two or more different web forums and they want to be able to hang out where their friends are.

Another possibility is a programmer or a hardware manufactures's rep, who might want to see  for themselves how their software or hardware is doing in different distros. They might want to be able to test how it works in different distros for themselves and give users advice. Even though the sofware seems the same, it may have some slight changes necessary for adapting it to different distros, for example we use 'sudo' in Ubuntu instead of running as root all the time. That might affect how software works so some software might need to be adapted for that. 

There could also be people who represent groups of others testing various distros to see which one will be the best for their company, or for their school or whatever.

There's probably lots of reasons for normally sane, sensible people would want to multi boot, but if you only want to get work done and keeping track of a more complicated setup isn't your cup of tea then multi booting would seem pretty silly really.

---

