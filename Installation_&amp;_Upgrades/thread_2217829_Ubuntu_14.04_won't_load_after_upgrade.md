---
title: "Ubuntu 14.04 won't load after upgrade"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by paulxx on 2014-04-18
I've just upgraded to 14.04. The upgrade told me to Restart to finish the upgrade but when I did I got a black screen with white writing with 4 lines beginning "mount:mounting..."etc, then "Target filesystem doesn't have requested /sbin/init"

I have a laptop with Windows 7 and a wubi installation of Ubuntu. I've been running 13.10 and before that 13.04 without any problems.

Any suggestions would be appreciated as I can't access Ubuntu at the moment.

paul.

---

### Post by creasywuqiong on 2014-04-18
I have the same problem...

---

### Post by kurttheviking on 2014-04-18
same problem here; same pattern (13.04 -> 14.04); will post if any of my attempted fixes work...

UPDATE: fwiw, i had to abandon the old wubi install and delete via add/remove programs. i then tried installing 14.04 using the wubi.exe within the new iso (loaded onto a usb stick) but, upon restart, hit the ol' "Serious errors were found while checking the disk drive for /". iso checksum's matched as expected ... I am beginning to wonder if something is amiss with dualbooting on win7 in general...

UPDATE: confirmed that 12.04 and 13.04 install as expected using the normal wubi.exe technique; however 14.04 continues to throw the /sbin/init error

---

### Post by michael.parrott94 on 2014-04-18
Also had the same problem with Windows 7, and a Wubi installation. I was upgrading from Ubuntu 12.04.

I found this [http://askubuntu.com/questions/159554/ubuntu-12-04-wont-load-hangs-at-busybox-v1-18-5-initramfs](http://askubuntu.com/questions/159554/ubuntu-12-04-wont-load-hangs-at-busybox-v1-18-5-initramfs) which I will try and report back.

---

### Post by hakuna_matata on 2014-04-21
Same problem, too.

I solve the problem by changing GRUB2 boot entry from "ro" to "rw"  e.g.
```
linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=AAC884AC1F144321 loop=/ubuntu/disks/root.disk **ro**   quiet splash $vt_handoff
```
to
```
linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=AAC884AC1F144321 loop=/ubuntu/disks/root.disk **rw**   quiet splash $vt_handoff
```

---

### Post by paulxx on 2014-04-21
Hello hakuna_matata, Can you explain exactly how to do this.

---

### Post by hakuna_matata on 2014-04-21
> **paulxx said:**
> Hello hakuna_matata, Can you explain exactly how to do this.
If you see GRUB2 menu with "Ubuntu" and other entries like [here (first picture) ]("https://help.ubuntu.com/community/Grub2"), you can press "e" to edit the commands before booting. 

There you can change the line as I described above. After changing press F10 to boot: [ Editing the GRUB 2 Menu During Boot]("https://help.ubuntu.com/community/Grub2/Troubleshooting#Editing_the_GRUB_2_Menu_During_Boot") 

edit: Depending on your configuration it is necessary for Wubi to hold down an arrow key after first menu (Windows boot menu) to see second menu (GRUB2).
edit2: "an arrow key" should be "shift key"

---

### Post by kurttheviking on 2014-04-21
> **hakuna_matata said:**
> edit: Depending on your configuration it is necessary for Wubi to hold down an arrow key after first menu (Windows boot menu) to see second menu (GRUB2).

which arrow key did you recommend? i just tried a clean install of 12.04 wubi then attempted upgraded to 14.04. upon reboot, it loads directly to the 

```

mount: mounting ... failed: Invalid argument
mount: mounting /dev on /root/dev failed ...
mount: mounting /sys on /root/sys failed ...
mount: mounting /proc on /root/proc failed: ...
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootarg.

(initramfs)

```

prompt, with no GRUB menu. I tried pressing each arrow key on boot but it loaded directly to the above.

UPDATE: holding down shift immediately after selecting Ubuntu from the windows boot loader brought up the GRUB screen.

UPDATE: I was able to change the boot command as described which booted into the desktop. However, upon restart I received the error:

```

Serious errors were found while checking the disk drive for /.

```

UPDATE: this was getting in the way of me doing work so I abandoned the wubi path, created a new partition for ubuntu (after burning my old recovery partition to disk, shrinking the primary partition, and merging the old recovery partition into the newly created space -- all because my laptop from lenovo came with 4 primary partitions so I couldn't just create a new extended partition)

---

### Post by hakuna_matata on 2014-04-21
> **kurttheviking said:**
> which arrow key did you recommend?

Sorry, it is not an arrow key, it is shift key.
  
> **kurttheviking said:**
> 
UPDATE: I was able to change the boot command as described which booted into the desktop. However, upon restart I received the error:

```

Serious errors were found while checking the disk drive for /.

```

It is only a temporary solution to boot into the desktop. If you need a permanent fix, you can change  **/etc/grub.d/10_lupin**
```
gksudo gedit  /etc/grub.d/10_lupin
```
Change the line 
```
    linux    ${rel_dirname}/${basename} root=${LINUX_HOST_DEVICE} loop=${loop_file_relative}** ro **${args}

```
to
```
linux    ${rel_dirname}/${basename} root=${LINUX_HOST_DEVICE} loop=${loop_file_relative}** rw **${args} 
```
save it and
```
sudo update-grub
```

---

### Post by MGSeattle on 2014-04-25
This is what has worked for me using hakuna's instructions.
Once you chose to boot into Ubuntu you will see two options:
[COLOR=#0000CD]***Ubuntu **[/COLOR](highlighted)[COLOR=#0000CD][B]
Advanced options for Ubuntu[/B][/COLOR]
Just press the '**[COLOR=#0000CD]e[/COLOR]**' key on your keyboard which will bring up the Grub menu.
Navigate using the arrow keys to the before last line
[COLOR=#000080]**linux /boot/vmlinuz-3.13.0-24-generic root=UUID=AAC884AC1F144321 loop=/ubuntu/disks/root.disk **[/COLOR][SIZE=4][COLOR=#B22222]**ro**[/COLOR][/SIZE][COLOR=#000080][B]   quiet splash $vt_handoff

[/B][/COLOR]replace[COLOR=#000080] [COLOR=#FF0000][SIZE=5]ro[/SIZE][/COLOR] [/COLOR]with[COLOR=#000080] [COLOR=#B22222][SIZE=5]rw [/SIZE][/COLOR][/COLOR][SIZE=5][/SIZE]then hit F10 your system will boot to Ubuntu[COLOR=#000080].[/COLOR]
In order not to have to do that every time you boot. Do this:
Open terminal an type:
```
gedit  /etc/grub.d/10_lupin
```
This will open the text editor with a bunch of code
Find the line [B][COLOR=#000080]linux    ${rel_dirname}/${basename} root=${LINUX_HOST_DEVICE} loop=${loop_file_relative}[FONT=Thread-00000f80-Id-0000001d] [/FONT][/COLOR][COLOR=#FF0000][FONT=Thread-00000f80-Id-0000001d][SIZE=4]ro[/SIZE][/FONT][/COLOR][COLOR=#000080][FONT=Thread-00000f80-Id-0000001d] [/FONT]${args}
[/COLOR][/B][COLOR=#000000]replace[/COLOR]**[COLOR=#000080][COLOR=#000080] [COLOR=#FF0000][SIZE=5]ro[/SIZE][/COLOR] [/COLOR][/COLOR]**[COLOR=#000000]with[/COLOR]**[COLOR=#000080][COLOR=#000080] [COLOR=#B22222][SIZE=5]rw [/SIZE][/COLOR][/COLOR][/COLOR]**[COLOR=#000080][COLOR=#000080][COLOR=#B22222][SIZE=5][/SIZE][/COLOR][/COLOR][/COLOR][COLOR=#000000][SIZE=5][/SIZE][SIZE=5][/SIZE]and save
then again in the terminal type
```
sudo update-grub
```
You're done. I hope this helps.
Thanks Hakuna.[/COLOR]

---

### Post by jaltman11 on 2014-05-03
These last two messages got me fixed, thanks much.

---

### Post by srmferreira on 2014-05-04
Thank you, hakuna_matata. 

In my system gedit isn´t installed. So I've done this little modification:
instead [B]

gksudo gedit  /etc/grub.d/10_lupin[/B]     

I had to use 
[B]
gksudo leafpad /etc/grub.d/10_lupin [/B]

or 
[B]
sudo leafpad /etc/grub.d/10_lupin 
[/B]
to acess this 10_lupin file.

I think **gedit** was replaced by **leafpad** in Lubuntu.

Thanks again, hakuna-matata. Now Lubuntu is starting well here.

---

### Post by foldes on 2014-05-04
I had the same problem and your post [#10]("http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696") solved it. One more addition. I had to add sudo before the gedit  /etc/grub.d/10_lupin    otherwise I couldn't save the change.
Thanks a lot.

---

### Post by mjz_inter on 2014-05-07
Thanks for your post, I tried what did you say, but i have a problem where Ubuntu does not allow me to save the file 
/etc/grub.d/10_lupin after editing it, saying that i am not the owner of this file and i dont have permition to save it. 

can you please advice how did you save the file after editing it? 

Thanks

---

### Post by ulysses768 on 2014-05-09
I have the same problem but I did not install through WUBI.  In fact I only have Ubuntu installed on my machine.
I upgraded to 14.04 from 13.10 and I have BTRFS as my root partition.  The only commonality between my system and the others is that I am using the signed UEFI vmlinuz.
When I boot legacy kernel executables on other machines I do not run into this issue.

For me, changing the grub option from rw to ro, just causes the system to hang.
If I choose to boot to the 3.11.0-19 kernel I have no problems, despite that option using "ro".

Unless I'm missing misunderstanding some major feature change between 3.11.0 and 3.13.0, this is a bug.
Does anyone know if this is being tracked?  I couldn't find anything on launchpad.

---

### Post by dennis21 on 2014-05-09
Thank you for helping we uber-noobs MGSeattle... much appreciated when all of the steps are listed. :D

---

### Post by hakuna_matata on 2014-05-09
> **ulysses768 said:**
> 
Does anyone know if this is being tracked?  I couldn't find anything on launchpad.
I know two bug reports:
[URL="https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/1317437"]
[/URL][https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1308152](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/1308152)
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/1317437](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/1317437)

IMHO reason for the bug are changes in busybox packages.

If you install old versions of busybox packages, there is no need for "rw"-changes.
```

wget http://archive.ubuntu.com/ubuntu/pool/main/b/busybox/busybox-initramfs_1.20.0-8.1ubuntu1_$(dpkg --print-architecture).deb
wget http://archive.ubuntu.com/ubuntu/pool/main/b/busybox/busybox-static_1.20.0-8.1ubuntu1_$(dpkg --print-architecture).deb
sudo dpkg -i busybox*1.20.0-8.1ubuntu1_$(dpkg --print-architecture).deb
sudo update-initramfs -u

```

---

### Post by ulysses768 on 2014-05-09
Thanks hakuna_matata.  Makes sense. I'll give it a try.  I had been compiling the kernel with saucy options to no avail.

---

### Post by ulysses768 on 2014-05-09
Unfortunately that did not end up fixing the problem.  Perhaps the issue is that my root partition btrfs partition is across two disks, although I've had that setup for nearly 3 years without an issue.

The first failure I see is
> (initramfs) mount: mounting /dev/disk/by-uuid/0048c... on /root failed: Invalid argument 

After I arrive at the (initramfs) prompt the mount command usually works. 
> (initramfs) mount /dev/disk/by-uuid/0048c... /root
If that fails I can mount atleast one of the two partitions by device name
> (initramfs) mount /dev/sda3


One out of every 15 times I am able to boot successfully. I am more likely to be successful with the recovery option. Perhaps there is a race condition?

---

### Post by hakuna_matata on 2014-05-10
> **ulysses768 said:**
> Perhaps the issue is that my root partition btrfs partition is across two disks, although I've had that setup for nearly 3 years without an issue.

Btrfs partition in connection with Wubi? Awesome! But IMHO it is another issue.

---

### Post by ulysses768 on 2014-05-11
I'm not using Wubi.  I should have made that more clear.  I just was seeing the same initramfs mounting failure.


If anyone is interested I have somewhat of a work around.  It seems I need to wait at least 10 seconds before selecting an option from the grub menu.  Apparently the multi-disk btrfs partition isn't ready to be mounted before then.
The fact that Grub does not recognize that the partition is not ready to be mounted appears to be a regression.  Adding a rootdelay (which is possibly deprecated anyway) has no effect since grub is not waiting for the partition to become available. 

Hopefully this horrible off-topic post will help someone.  A quick search of 'debian initramfs btrfs' yields similar recent issues with 3.14, so this apparently effects multiple people.  Hopefully a true fix is in the works.

---

### Post by Paul_C_Burr on 2014-05-16
Thank you. I'm a newbie to Ubuntu/Linux. I "had" the exact same problem on my Samsung NC10. I haven't done any systems programming in 35 years.
I followed your clear instructions and the problem is solved.
I very much appreciate your help.

---

### Post by kei-kanzawa on 2014-05-21
Dear Hakuna, MGSeattle,

I installed ubuntu14.04 to my wondows7 using wubi.

as your instruction, I wrote
```
sudo gedit /etc/grub.d/10_lupin
```

then I replaced ro with rw on that line and saved.

finally, I wrote
```
sudo update-grub
```

but I still need to press "e" button and replace ro with rw every time I boot.

Why is it? Thanks in advance.

---

### Post by kei-kanzawa on 2014-05-21
I think you need "sudo" before/etc/grub.d/10_lupin to save the changes

---

### Post by Jimiteru on 2014-05-24
not /etc/grub.d/10_lupin, but /boot/grub/grub.cfg

---

### Post by milan7 on 2014-05-25
I opened the terminal and put in the code to replace O with W in order to boot without having to go thru typing the E key in order to boot. I changed the O with the W, but it wont let me save the file. It says "You do not have the permission to save the file. Please check that you typed the location correctly and try again". How do I fix this?
Thank You

---

### Post by Jimiteru on 2014-05-25
> **milan7 said:**
> I opened the terminal and put in the code to replace O with W in order to boot without having to go thru typing the E key in order to boot. I changed the O with the W, but it wont let me save the file. It says "You do not have the permission to save the file. Please check that you typed the location correctly and try again". How do I fix this?
Thank You

What is the command you typed? Did you put "sudo" in front of the command? You need to be a super user(su) to change and save the file you want to edit.

---

### Post by Comet220 on 2014-05-28
I've had the same problem installing ubuntu 14.04 and I want to try the solution here but I've never done any programming or used command line before. I followed pretty much everything MGSeattle posted but I don't know how to save changes. Do you just press enter?

---

### Post by hakuna_matata on 2014-05-29
> **Comet220 said:**
> I followed pretty much everything MGSeattle posted but I don't know how to save changes.
```
gedit  /etc/grub.d/10_lupin
```
should be
```
[SIZE=4]**gksudo**[/SIZE] gedit /etc/grub.d/10_lupin
```

---

### Post by saumye_mehrotra on 2014-06-02
> **hakuna_matata said:**
> ```
gedit  /etc/grub.d/10_lupin
```
should be
```
[SIZE=4]**gksudo**[/SIZE] gedit /etc/grub.d/10_lupin
```



i saved these changes but when you said to do this in post #10 ```
sudo update-grub
```
so that i dont have to do it again and again it says bad substitution and i have to press 'e' at the grub menu and change it everytime i boot my pc...

---

### Post by Jimiteru on 2014-06-02
> **saumye_mehrotra said:**
> i saved these changes but when you said to do this in post #10 ```
sudo update-grub
```
so that i dont have to do it again and again it says bad substitution and i have to press 'e' at the grub menu and change it everytime i boot my pc...

Dear saumye_mehrotra,

Did you try change /boot/grub/grub.cfg already?
You should try to replace first ro with rw and save it.
I couldn't solve it by changing /etc/grub.d/10_luipn, but I solved it by changing /boot/grub/grub.cfg.
I don't have to press "e" before boot any more.
The code you should change in grub.cfg below
```
linux	/boot/vmlinuz-3.13.0-24-generic root=UUID=5E028ABC028A9923 loop=/ubuntu/disks/root.disk _**rw**_ rootflags=sync  quiet splash $vt_handoff
```

---

### Post by hakuna_matata on 2014-06-02
> **Jimiteru said:**
> 
I couldn't solve it by changing /etc/grub.d/10_luipn, but I solved it by changing /boot/grub/grub.cfg.

It is also possible to change  /boot/grub/grub.cfg, but every time you make
```
sudo update-grub
```
you will loose your changes.

Additionally, some updates will create a new  /boot/grub/grub.cfg, too. (e.g. new kernel packages). The changes in /etc/grub.d/10_lupin are safer. if you don't install or update your package lupin-support, your changes will be still alive in the future.

It is also possible to change /etc/grub.d/10_lupin and update  /boot/grub/grub.cfg with the following commands;
```

sudo sed -i s/' ro '/' rw '/g /etc/grub.d/10_lupin
sudo update-grub

``` 
The advantage is that there is no need to search for "ro" and change it manually. Drawback is the cryptical "sed" command for beginners.

edit: 
If your changes don't work, please check the leading and trailing spaces:
    
```
    linux    ${rel_dirname}/${basename} root=${LINUX_HOST_DEVICE} loop=${loop_file_relative} rw ${args}
```

---

### Post by hakuna_matata on 2014-06-06
Meanwhile a bugfix exists: [http://bazaar.launchpad.net/~noorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437/revision/281](http://bazaar.launchpad.net/~noorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437/revision/281)

Thanks to Noorez Kassam.

---

### Post by Supersonicx10 on 2014-06-14
What do you mean by "open the terminal"? is it the command-line?

---

### Post by hakuna_matata on 2014-06-14
> **Supersonicx10 said:**
> What do you mean by "open the terminal"? is it the command-line?
[URL="https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal"]Starting a Terminal
[/URL]

---

### Post by megapooser on 2014-06-26
Whenever I input "gedit  /ect/grub.d/10_lupin" into my terminal it brings up a message telling me that this file has been edited and wont let me do anything else.

---

### Post by hakuna_matata on 2014-06-27
> **megapooser said:**
> Whenever I input "gedit  /ect/grub.d/10_lupin" into my terminal it brings up a message telling me that this file has been edited and wont let me do anything else.
Try your command with two differences (highlighted):
```
**gksudo** gedit /e**tc**/grub.d/10_lupin
```

---

### Post by LibertarianBiker on 2014-07-06
Thanks MGSeattle and Hakuna!

for some when I type 
gedit  /etc/grub.d/10_lupin

in the terminal window, it opens read only.  Any ideas why it would do that?

---

### Post by hakuna_matata on 2014-07-07
> **LibertarianBiker said:**
> 
for some when I type 
gedit  /etc/grub.d/10_lupin

in the terminal window, it opens read only.  Any ideas why it would do that?
Please use 
```
gksudo gedit  /etc/grub.d/10_lupin
```
as I wrote some posts above. 

Only SuperUser named **Root **can change**   /etc/grub.d/10_lupin**. Use "gksudo" to start graphical applications as Root.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by manny7 on 2014-07-19
Thank you so much... It works perfectly on my part... Now I'm using Linux 17

---

### Post by farfar3 on 2014-08-08
[SIZE=4][FONT=georgia]Hi,

First of all I should say I am new to Linux.
[/FONT][/SIZE][SIZE=4][FONT=georgia]I installed Ubuntu Wubi 12.10 on my desktop.[/FONT][/SIZE]Yesterday I attempted to upgrade my Ubuntu 12.10 to 14.04. 

[SIZE=4][FONT=georgia]Everything  went okay, up until the point I had to reboot to make the update work. After that, I cannot boot into Ubuntu due to this error:[/FONT][/SIZE]
mount: mounting ... failed: Invalid argument
mount: mounting /dev on /root/dev failed ...
mount: mounting /sys on /root/sys failed ...
mount: mounting /proc on /root/proc failed: ...
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootarg.

(initramfs)
[SIZE=4][FONT=georgia]
[/FONT][/SIZE][SIZE=4][FONT=georgia]Then I googled it and found boot repair tool. after I used it it gave me this link :

[URL="http://paste.ubuntu.com/7992402/"]http://paste.ubuntu.com/7992402/
[/URL]
(In this link there is some properties of my OS and  Boot Info Script ...)

And after rebooting my system then this message appeared to the screen :
It says something like:

"Serious errors were found while checking the disk drive for /.
pressI to ignore, S to skip and M for manual recovery." 

If I ignore it, 

then another message pops up saying 
"[COLOR=#333333]The disk drive for /tmp is not ready yet or not present[/COLOR]". 
I also tried pressing "shif key" on boot to go to Grub but it loaded directly to the above...
So this solution can't work for me.
when I press M to recover it manulally then I shouldn't what I should do ?
I also see this link 
[http://elementaryos.org/answers/the-disk-drive-for-tmp-is-not-ready-yet-or-not-present](http://elementaryos.org/answers/the-disk-drive-for-tmp-is-not-ready-yet-or-not-present)
to solve it but when I try (sudo mv /tmp /tmp_old) it said that :
can not move '/tmp' to '/tmp_old':
read-only file
when I use chmod 777 /tmp
again the same problem will come to screen

I also tried others solution...but nothing changed 

Actually I don't know how to solve this problem. 

Would you please help me?

So many thanks in advance for your help.

[/FONT][/SIZE]

---

### Post by hakuna_matata on 2014-08-09
> **farfar3 said:**
> 
[SIZE=4][FONT=georgia][SIZE=2][SIZE=4][FONT=georgia][SIZE=2]"Serious errors were found while checking the disk drive for /.
pressI to ignore, S to skip and M for manual recovery." [/SIZE]
[/FONT][/SIZE][/SIZE][/FONT][/SIZE]
In a lot of cases this previous post is helpful: [http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696](http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696)

IMHO the easiest way for you should be to boot an old kernel version.
In Ubuntu Grub menu select**[B] "Advanced options for Ubuntu" **[/B](instead of "**Ubuntu**") and"**Ubuntu, with Linux 3.8.0-44-generic** (instead of "**Ubuntu, with Linux 3.13.0-32-generic**")

If you can boot, just copy and paste these two lines in a terminal to change boot options for future boot with default menu entry "Ubuntu":
```

sudo sed -i s/' ro '/' rw '/g /etc/grub.d/10_lupin
sudo update-grub

```

---

### Post by farfar3 on 2014-08-11
Hi,
THANKS a lot for your reply.
after my ubuntu booted, I PRESS M for manually recovered and go to terminal.
and then write the command you told me "sudo sed -i s/' ro '/' rw '/g /etc/grub.d/10_lupin"
but this appears:
sed: couldn't open temporary file /etc/grub.d/sedMz1Erj: read-only file system

So would you tell mw what should I  do now?
Thanks a lot.

---

### Post by farfar3 on 2014-08-11
I also try mount -o remount /
but it gives me this error:
cannot remount block device /dev/loop 0 read-write, is write protected.
I ALSO use chmod for that but it doesnot work. [IMG]http://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]

So would you tell me what should I  do now?

---

### Post by hakuna_matata on 2014-08-12
> **farfar3 said:**
> 
after my ubuntu booted, I PRESS M for manually recovered and go to terminal.

First of all, you should boot _without_ errors to _desktop enviroment_. If you can do so, the sed command is for your terminal. The sed command doesn't work in rescue enviroment without write access.

So the first start without errors should be with one of these instructions: 

[http://askubuntu.com/questions/454143/upgraded-to-14-04-reboot-fail](http://askubuntu.com/questions/454143/upgraded-to-14-04-reboot-fail)
[http://askubuntu.com/questions/452631/ubuntu-14-04-doesn-t-boot-after-upgrade-from-12-04-installed-inside-windows-8-1](http://askubuntu.com/questions/452631/ubuntu-14-04-doesn-t-boot-after-upgrade-from-12-04-installed-inside-windows-8-1)
[http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696](http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696)

Or my suggestion:
> In Ubuntu Grub menu select**[B] "Advanced options for Ubuntu" **[/B](instead of "**Ubuntu**") and"**Ubuntu, with Linux 3.8.0-44-generic** (instead of "**Ubuntu, with Linux 3.13.0-32-generic**")

---

### Post by noodletaboo on 2014-09-24
Hi!

I'm experiencing the same problem. The patch of replacing ro to rw works, but it doesn't work when I permanently edit this "10_lupin" file. The file is saved and edited permanently, but when I try to restart normally, then I have this purple screen of loading ubuntu but not being able to mount, it says: serious errors were found while checking drive for / and asking me if I want to ignore, skip or do it manually. And later the disk drive for /tmp is not ready yet or not present...

As far as my logic gets, it seems that the file that I'm editing permanently (10_lupin) is not the same as the one I edit each time at the start with the Grub2. Altough the file 10_lupin is permanently edited with "rw", still in the Grub2 in the start needs to be changed again.

Any idea? thanks =D

---

### Post by merhawifissehaye on 2014-09-25
Perfect. I used to press e and edit grub setting every time I start my system. Now I have permanently solved the problem by edit /etc/grub.d/10_lupin with elevated privilege and update-grub command.
Thank you

---

### Post by hakuna_matata on 2014-09-25
> **noodletaboo said:**
> 
As far as my logic gets, it seems that the file that I'm editing permanently (10_lupin) is not the same as the one I edit each time at the start with the Grub2.
You are right. Grub2 doesn't use **/etc/grub.d/10_lupin**, it uses[B] /boot/grub/grub.cfg.

[/B]But
> sudo update-grub
updates **/boot/grub/grub.cfg **and therefore it uses all executable scripts in folder **/etc/grub.d **including **/etc/grub.d/10_lupin**

---

### Post by noodletaboo on 2014-09-26
You're totally right Hakuna Matata,

I saved the file 10_aline but I didn't used that command in the end. So I applied "sudo update-grub" and now it is working fantastic. 

Thanks a lot for your help! =D

---

### Post by D_k_Surbaugh on 2014-09-30
okay, so I am having the same issues:
> [I]mount: mounting /dev on / root /dev failed: No such file or directory 
mount:mounting /sys on /root sys failed No such file or directory 
mount: mounting / Proc on /root /proc failed: No such file or directory 
 Target file system doesn't have requested  /sbin /init. 
No init found. Try passing=bootarg. 
Busybox.  v1.21.1 (ubuntu 1:1.21.0-1ubuntu1) built-in shell cash [/I]
However, I don't have the Advanced in my Master Boot.  I only have Windows 7 and Ubuntu as my only two options.  The "e" key doesn't do anything while in the Master Boot with Ubuntu highlighted.  So what do I do, besides uninstalling and going back to the previous version.

---

### Post by hakuna_matata on 2014-10-01
> **D_k_Surbaugh said:**
> 
However, I don't have the Advanced in my Master Boot.  I only have Windows 7 and Ubuntu as my only two options.
There are two different menus. The first menu is part of Windows Boot Manager. The second menu is part of Grub2. You need second one. If second one is hidden, press the Shift key immediately after selecting "Ubuntu" in the first one.

---

### Post by Crugster on 2014-10-03
I'm not sure whether this post will be considered thread pollution or courtesy; but I wanted to say *thanks* nevertheless (and there is no "thanks" / kudo button on this forum)!

Especially post [#10]("http://ubuntuforums.org/showthread.php?t=2217829&p=13001696#post13001696") and surrounding posts, e.g. the ones explaining that pressing the [Shift] after selecting Ubuntu (in the windows boot menu) unhides GRUB, solved the issue for me  (actually for my dads) too. So here it goes:

**THANKS - You guys/gals rock** (this is why I love the Linux community)!

---

### Post by spirit12 on 2014-10-27
I have this problem after upgrade to 14.04 from 12.04 via upgrade app. My 10. lopin file is empty so I cannot edit the line to rw. The system is booted initialy in read only to be able to perform checksum then later in the boot process it is mounted read/write & it seems  to me this is the point at which the fault is & may be the reason for the error messages seen by some. I in fact have two systems running this both having been updated to 14.04. The other system works perfectly & interestingly these files that are being edited to solve the boot problem are identical on the one that works & the on that dose not. They are all set to ro on both. Any idea why my 10.lopin is empty on both systems & any idea where the setting is to mount in read/write later in the boot process after checksums have been done?

---

### Post by hakuna_matata on 2014-10-27
> **spirit12 said:**
> Any idea why my 10.lopin is empty on both systems
**10.lopin** ? Do you mean **/etc/grub.d/10_lupin** ?

---

### Post by Austin_Diamond on 2014-11-01
I have been using the advice in this forum following a failed upgrade from Ubuntu 12.04 to 14.04 on a dual-boot (Win7) installation.
- and would also like to add my thanks to all those who have contributed, I am new to trying Ubuntu/Linux and find it very reassuring to have  this community support.

I get the following message when trying the solution suggested:

[I]austin@ubuntu:~$ sudo sed -i s/' ro '/' rw '/g /etc/grub.d/10_lupin
[sudo] password for austin: 
austin@ubuntu:~$ sudo update-grub
GRUB >= 2.00 has been unpacked but not yet configured.
grub-mkconfig will not work until the upgrade is complete.
It should run later as part of configuring the new GRUB packages.
austin@ubuntu:~$ [/I]

When I try to re-boot I my changes have not been saved and I still need to press "e" and change "ro" to "rw".

What should I do next?

Thank you

---

### Post by hakuna_matata on 2014-11-01
> **Austin_Diamond said:**
> 
[I]austin@ubuntu:~$ sudo update-grub
GRUB >= 2.00 has been unpacked but not yet configured.
grub-mkconfig will not work until the upgrade is complete.
It should run later as part of configuring the new GRUB packages.
austin@ubuntu:~$ [/I]

If **update-grub** doesn't work, it is possible to update** /boot/grub/grub.cfg **with
```
sudo sed -i s/' ro '/' rw '/g /boot/grub/grub.cfg
```
This will solve your current issue:
> **Austin_Diamond said:**
> When I try to re-boot I my changes have not been saved and I still need to press "e" and change "ro" to "rw".
But you need a working **grub-update** after kernel updates, too

Maybe there are broken packages and you can repair this with
```

sudo apt-get -f install 
sudo dpkg --configure -a 
sudo apt-get update 
sudo apt-get upgrade

```

---

### Post by The Frenchman on 2014-11-26
> **spirit12 said:**
> I have this problem after upgrade to 14.04 from 12.04 via upgrade app. My 10. lopin file is empty so I cannot edit the line to rw. The system is booted initialy in read only to be able to perform checksum then later in the boot process it is mounted read/write & it seems  to me this is the point at which the fault is & may be the reason for the error messages seen by some. I in fact have two systems running this both having been updated to 14.04. The other system works perfectly & interestingly these files that are being edited to solve the boot problem are identical on the one that works & the on that dose not. They are all set to ro on both. Any idea why my 10.lopin is empty on both systems & any idea where the setting is to mount in read/write later in the boot process after checksums have been done?
I recently did the same upgrade and since then boot to Lubuntu OK, but every time get system prog problem detected,report problem? message and then, sorry ubuntu 14.04 internal error /sbin/init.I did report a few times but as my netbook then carries on working as normal,is it OK just to click on ignore?

---

### Post by nahidbigboss on 2014-11-29
thank you !! worked :-x

---

### Post by dcharlespyle on 2015-01-07
So everyone knows, the rw change in grub can cause issues with recovery options should you ever need to use some of them.  While the rw modification is good to get one in the door, so to speak, one should not edit the /etc/grub.d/10_lupin file as given above.  I myself used to do that until I found that certain recovery options stopped working after the change, when I needed them most.  A better approach to making changes that allows 14.04 LTS users to boot permanent is to edit the /usr/share/initramfs-tools/scripts/local file.  Before doing the below, anyone who made the ro -> rw change in the /etc/grub.d/10_lupin file should undo it and revert the line back to ro but do not yet reboot.  After doing that, do the following:

1.  Open in your favorite editor as root superuser your /usr/share/initramfs-tools/scripts/local file.  Look for the line that reads as follows:

mount ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt}

2.  Comment out that line and add the following three lines below that line:

        loopdev=`losetup -f`
        losetup ${loopdev} "/host/${LOOP#/}"
        mount ${roflag} -t ${FSTYPE} ${LOOPFLAGS} ${loopdev} ${rootmnt}

3.  Save the file and run in a terminal:  **sudo update-grub**.

After that, you can reboot your system and you should be good to go whenever kernel updates come around, and you will be able to use recovery options as they should be used.  Make sure to make a backup of the edited file in case an upgrade removes your changes.  That way, if an upgrade manages to break your changes, you can copy the modified lines in the backed up file and place them in the proper location.  Hope this helps.

---

### Post by hakuna_matata on 2015-01-08
> **dcharlespyle said:**
> A better approach to making changes that allows 14.04 LTS users to boot permanent is to edit the /usr/share/initramfs-tools/scripts/local file.
You are right. It is a better solution and it would be the easiest solution if this patch would be part of official package [initramfs-tool]("http://packages.ubuntu.com/initramfs-tool"). Maybe, you can help us to push [this patch]("https://code.launchpad.net/~noorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437").

Currently, IMHO there are two disadvantages:
[LIST]
[*]Every new version of package [initramfs-tool]("http://packages.ubuntu.com/initramfs-tool") overwrites your changes. Of course, every change of [lupin-support]("http://packages.ubuntu.com/lupin-support") overwrites changes in  **/etc/grub.d/10_lupin**, too. But IMHO these changes are less frequently than changes in [initramfs-tool]("http://packages.ubuntu.com/initramfs-tool") 
[*]It is easier for beginners to replace ro by rw than one command by three commands. In addition, it should be easier to understand what ro (read only) and rw (read and write) mean. 
[/LIST]
 
I use [this patch]("https://code.launchpad.net/%7Enoorez-kassam/ubuntu/utopic/initramfs-tools/fix-for-1317437") but I wrote a script which patches automatically the file **/usr/share/initramfs-tools/scripts/local** to avoid surprises after updates.

[LIST=1]
[*]I created a file **/etc/initramfs-tools/hooks/loop-remount** ```
gksudo gedit  /etc/initramfs-tools/hooks/loop-remount 
``` 
[*]I Inserted the following lines: 
[/LIST]
```
 #! /bin/sh
set -e

filename="/usr/share/initramfs-tools/scripts/local"
oldvalue='mount ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt}'
newvalue='loopdev=`losetup -f`; losetup ${loopdev} "/host/${LOOP#/}"; mount ${roflag} -t ${FSTYPE} ${LOOPFLAGS} ${loopdev} ${rootmnt}'

if [ -f $filename ]; then
   if cat $filename | grep "$oldvalue" >/dev/null; then
      sed -i "s%$oldvalue%$newvalue%g" $filename
   fi
fi

exit 0
```
3. I saved it and ran my new script and updated initramfs which is available at boot time ```
sudo /etc/initramfs-tools/hooks/loop-remount
sudo update-initramfs -u

```

---

### Post by moises5 on 2015-02-24
Hello:
For some months, I worked with version 12.04 LTS and last week I decided to upgrade to 14.04 LTS version. After completing the upgrade, I got the mounting error you are talking about in this thread. Now I have the "serious error were found while checking the disk" thing. I enter the Grub (version 2.02) by pressing "shift" cap, I press "e" and I change "r" line for "w" in order to be able to sign in. I press F10 and takes me to the login screen in Ubuntu. I had several choices as Ubuntu, Lubuntu, Lubuntu netbook, Ubuntu 2d, etc. but now only have three; Lubuntu, Lubuntu netbook and Open. I choose Lubuntu Netbook, write the password and press enter and I get an error message (only options, send or cancel) and the thing gets frozen. I try to enter Grub and use another kernel but I have only one version of it (3.13.0-45, "normal" and "recovery mode" option) so I can't progress. I'm in a dead-end. If I enter the recovery mode I have an option to repair the boot but I haven't do it for fear of worsening the problem. Any Idea? :-(
Thanks in advance

---

### Post by hakuna_matata on 2015-02-24
> write the password and press enter and I get an error message (only options, send or cancel) and the thing gets frozen.
IMHO it is an additional issue which does not depend on Wubi. There are several reasons for errors after an upgrade.

In this case, it is a better solution to fix the mounting bug with [URL="http://askubuntu.com/a/552041"]this solution.

[/URL]There is no need for a graphical enviroment. You should get a none graphical enviroment by pressing Ctrl + Alt + F1 _or_ Ctrl + Alt + F2 _o_r Ctrl + Alt + F3 ..... at login screen. You can use  
```
sudo nano /usr/share/initramfs-tools/scripts/local
```
and change
```

mount ${roflag} -o loop -t ${FSTYPE} ${LOOPFLAGS} "/host/${LOOP#/}" ${rootmnt}

```
to
```

loopdev=`losetup -f`        
losetup ${loopdev} "/host/${LOOP#/}"
mount ${roflag} -t ${FSTYPE} ${LOOPFLAGS} ${loopdev} ${rootmnt}
``` as described by bcbc

After that you can use recovery mode in read-only mode with the option to change to read-write mode. 
 > but I haven't do it for fear of worsening the problem.
If you have a backup of your install, this should be not possible.

---

### Post by hurin8888 on 2015-03-18
Hello I am using ubuntu as a secondary OS and use windows 8.1 boot loader, I don't have the grub files mentioned in this thread and none of the solutions work for me. Thank you for helping me.

edit: found the grub file and solved the problem

---

