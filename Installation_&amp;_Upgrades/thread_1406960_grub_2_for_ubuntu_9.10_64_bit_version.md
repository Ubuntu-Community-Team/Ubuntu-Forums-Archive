---
title: "grub 2 for ubuntu 9.10 64 bit version"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by ljupcho on 2010-02-14
Hello,
I am experiencing problems installing ubuntu 9.10 64 bit.
First I downloaded `ubuntu-9.10-desktop-amd64.iso` from the official site (not torrent). I installed it OK with specifying partitions for ubuntu and swap area.
Then I couldn’t boot into ubuntu because I am not having the grub restored.
After reading some tutorials, what I did was:
sudo fdisk –l
I check here that my ubuntu partition is /dev/sad6. 
sudo mount | tail –l
and check for mounting my ubuntu  partition.
/dev/sda6 on /media/0d104aff-ec8c-44c8-b811-92b993823444 type ext4 (rw,nosuid,nodev,uhelper=devkit)

I copy the “0d104aff-ec8c-44c8-b811-92b993823444” part and do this:
sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda

I tried this with `mkdir` aswell : 
sudo mkdir /media/sda6
sudo mount /dev/sda6  /media/sda6
sudo grub-install –root-directory=/ media/sda6 / dev/sda

then I do the usual:
sudo grub
grub> find /boot/grub/stage1
(hd0,5)
grub> root  (hd0,5)
grub>setup (hd0)   (or setup(hd0,5))
grub> quit


Well, it turns out that this doesn’t work for me. Any ideas why wouldn't this work, because when I reboot I am getting only the grub prompt and I don’t know what to do with it?
Furthermore I read that it might be because my UBUNTU OS is using grub legacy not grub2 and that I need to boot with ubuntu 9.04 live cd and do the same. I did that as well and again I am getting only the grub prompt.
Can anyone help me and verify if I am doing this right or I am missing some steps?

Thanks,
Ljupcho

---

### Post by darkod on 2010-02-14
You should have used only this:
sudo mkdir /media/sda6
sudo mount /dev/sda6  /media/sda6
sudo grub-install –root-directory=/ media/sda6 / dev/sda

The commands you used after that are for grub1 I think and it might have messed things up for you.
Read here in post #2 my instructions how to run the script and post your results here.

---

### Post by ljupcho on 2010-02-14
hi,
thank you for your reply.
From the file att. i don't quite understand this part:
 Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 353054022 of the same hard drive for 
                       the stage2 file. A stage2 file is at this locationon 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.

Do I need to migrate the grub to ver.2?
Thanks.

---

### Post by darkod on 2010-02-15
> **ljupcho said:**
> hi,
thank you for your reply.
From the file att. i don't quite understand this part:
 Boot sector info:  Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 353054022 of the same hard drive for 
                       the stage2 file. A stage2 file is at this locationon 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.

Do I need to migrate the grub to ver.2?
Thanks.

I'll have to look at it later, I'm on windows now and the formatting doesn't show correct on windows. Or you could open the file, just copy all the content (text), post it inside a reply and while it is still selected hit the # button in this toolbar above when writing a reply. That will post the whole text inside CODE tags.

The part you quoted means you have grub1 (off ver number 0.97) on the partition /dev/sda6. Usually it's best the bootloader to be on the MBR of the hdd and no other bootloaders to be on the actual partitions. There are exceptions if needed.

I can't say more before seeing the complete results.

---

### Post by darkod on 2010-02-15
OK, I managed to get a look at the results file. Grub1 got installed on /dev/sda6 because in the third group of commands you posted you executed setup (hd0,5) instead of setup (hd0).
But those commands are for the older grub1 anyway so I won't explain them now.

To get your dual boot up and running, boot with the ubuntu 9.10 cd, Try Ubuntu option, and in terminal execute:

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That will install grub2 to the MBR of /dev/sda. Reboot without the cd and you should get grub menu allowing you to select ubuntu or windows. Check if it's working fine.

---

### Post by ljupcho on 2010-02-15
those 2 commands did get me back the grub menu for selection, but ununtu is not bootable!
It is the starting point where i was after installing ubuntu.
I did again the find /boot/grub/stage1 with setup (hd0) -> that brings me back the grub prompt.

so, please, do you have any other suggestions about if ubuntu 9.10 64bit can actually work?

thanks.

---

### Post by darkod on 2010-02-15
setup (hd0) is used for grub1, not for grub2 that 9.10 uses. Don't run commands for grub1 or you'll get into even bigger mess.
If ubuntu didn't boot you should have explained bit more what exactly is the problem, any error messages, etc. Not to execute grub1 commands.
I'm sorry, but "ubuntu is not bootable" doesn't tell anything.

---

### Post by recluce on 2010-02-15
It should be mentioned at least that the other alternative would be to ditch GRUB2 and revert to Legacy GRUB completely.

All the remarks to the contrary withstanding, Legacy GRUB works perfectly with EXT4 file systems and boots Karmic and Lucid like a charm. Glad to help if you want go that way.

---

### Post by ljupcho on 2010-02-15
> **recluce said:**
> It should be mentioned at least that the other alternative would be to ditch GRUB2 and revert to Legacy GRUB completely.

All the remarks to the contrary withstanding, Legacy GRUB works perfectly with EXT4 file systems and boots Karmic and Lucid like a charm. Glad to help if you want go that way.

yes, please, post me the commands.

---

### Post by recluce on 2010-02-16
I assume for now that you cannot boot Ubuntu. If you can, there is a "cleaner" method of replacing GRUB2 with Legacy GRUB.

You need an Ubuntu 9.04 (Jaunty) Live CD to follow the instructions in this guide:

[http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD](http://members.iinet.net.au/~herman546/p15.html#Re-install_Grub_with_Live_CD)

Be sure it is 9.04. Earlier versions of the live CD will have a GRUB that is incompatible with EXT4 partitions, 9.10 will have GRUB2.

Basically, you need to boot up the Live CD, mount the partition you want to install the grub files to (your Ubuntu partition) and use the following command:

sudo grub-install --root-directory=/media/disc /dev/sdb

"/media/disc" can vary, this is the path were /boot is located
"/dev/sdb" - replace "sdb" by whatever is your primary drive, the one the computer should boot from.

After this, you need to setup grub (while still running your live session). This is also explained in the next section of the same guide. The commands in short:

sudo grub

You will see a grub shell prompt "grub >". Type

find /boot/grub/stage1

grub will respond with some thing like "hd(0,4)". This is where your Ubuntu partition is located. Note that the count starts with zero, not with one. You may see multiple replies if you have more than one Linux partition. Now type:

root hd(x,y)

"x" and "y" are the location of your boot partition, see above. Now type:

setup hd(x)

More details in the guide I linked for you. You may have to edit the menu.lst file to manually enter operating systems that GRUB missed. Also, while GRUB2 will not be active, all the GRUB2 files will still be in your /boot/grub folder. If you play around a lot with your Linux installation or have multiple Linux installations on one machine, you might want to setup a dedicated GRUB partition, which is explained in the same guide. This has the advantage that GRUB is not wiped by every new Linux installation you do.

---

### Post by ljupcho on 2010-02-18
hi,
i think i know what the problem is and the solution, but i need to ask something.
i think it is the acpi=off that i need to set up in the /etc/default/grub file, since i can boot with acpi=off from live cd i think i need to have it that in this file as well.
so i did:
gksudo gedit /etc/default/grub

in it i modified:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash,acpi=off"

and after this i need to update the grub. I found this command:sudo grub-mkconfig -o /boot/grub/grub.cfg
but i get this error:
"grub-probe: error: cannot find a device for /."

also i did: sudi -i
that gave me the root, did the update-grub, but got the same error message:
"grub-probe: error: cannot find a device for /."

i would search for what i should do more on net about this error, but do you guys can wrap it up for me! how do i update the grub, so my changes would take effect?

thanks,
ljupcho

---

### Post by oldfred on 2010-02-18
I do not think you need the comma.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off" 			 		

Ar you now going with grub2 not grub legacy? Will the liveCD let you boot the hard drive Ubuntu where it gives choices?

---

### Post by ljupcho on 2010-02-19
I am having the grub list of OS to choose from, i just can't reconfigure the /etc/default/grub file.
I guess i shouldn't be running the "sudo apt-get install grub" command, since i stick to grub2 which is installed by default.
i can't get pass by this error for now:
"grub-probe: error: cannot find a device for /."
i can't find any useful post for this!

---

### Post by oldfred on 2010-02-19
I do not think we can tell if you are on old grub or grub2. If you keep installing grub over grub2 it will never work. And usually if you have both installed neither will work.

---

### Post by kansasnoob on 2010-02-19
> **oldfred said:**
> I do not think we can tell if you are on old grub or grub2. If you keep installing grub over grub2 it will never work. And usually if you have both installed neither will work.

+1! It won't work right if you have mixed legacy grub and grub2 files in the grub directory.

It's easy to see. Just run "ls /boot/grub" and if you see both a menu.lst and a grub.cfg things are mixed.

To see which flavor of grub is handling (or trying to handle) boot you can run "grub-install -v".

To see what grub packages are installed you can use "aptitude show <package-name>|head -4" (works with any package).

My lazy way:

```
grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4
```

Note that both legacy grub and grub2 use the package "grub-common". The package "grub" is legacy grub and the package "grub-pc" is grub2.

If I find that things are hosed I just refer to this:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Note that appendix #2 briefly describes going from legacy grub to grub2.

---

### Post by ljupcho on 2010-02-19
After running the commands i got this:

ubuntu@ubuntu:~$ ls /boot/grub
device.map  grubenv
ubuntu@ubuntu:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)
ubuntu@ubuntu:~$ aptitude show grub|head -4
Package: grub
State: not installed
Version: 0.97-29ubuntu59
Priority: optional
ubuntu@ubuntu:~$ aptitude show grub-pc|head -4
Package: grub-pc
State: installed
Automatically installed: yes
Version: 1.97~beta4-1ubuntu3
ubuntu@ubuntu:~$ aptitude show grub-common|head -4
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.97~beta4-1ubuntu3


So, I have grub-pc installed. my grub.cfg file is under /boot/grub/grub.cfg
I suspect that my problem is in /etc/default/grub file where I need to configure:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off" with root access, but I don't know how to update the grub itself after this.
From the GRUB2 tutorial I need to run only 'update-grub' but that gives me that error: "grub-probe: error: cannot find a device for /."
How do I update the grub2 or grub-pc actually?

---

### Post by ljupcho on 2010-02-19
> **ljupcho said:**
> After running the commands i got this:

ubuntu@ubuntu:~$ ls /boot/grub
device.map  grubenv
ubuntu@ubuntu:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)
ubuntu@ubuntu:~$ aptitude show grub|head -4
Package: grub
State: not installed
Version: 0.97-29ubuntu59
Priority: optional
ubuntu@ubuntu:~$ aptitude show grub-pc|head -4
Package: grub-pc
State: installed
Automatically installed: yes
Version: 1.97~beta4-1ubuntu3
ubuntu@ubuntu:~$ aptitude show grub-common|head -4
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.97~beta4-1ubuntu3


So, I have grub-pc installed. my grub.cfg file is under /boot/grub/grub.cfg
I suspect that my problem is in /etc/default/grub file where I need to configure:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off" with root access, but I don't know how to update the grub itself after this.
From the GRUB2 tutorial I need to run only 'update-grub' but that gives me that error: "grub-probe: error: cannot find a device for /."
How do I update the grub2 or grub-pc actually?

PS.
Also, i don't know why are only two files listed after "ls /boot/grub"?
I cannot open the grub.cfg (which is also in that folder), with the command: sudo gedit /boot/grub/grub.cfg, but I have to browse to that path and open it manually!
Is there any trick to this or i should just run another install of Ubuntu.
Strange if ubuntu didn't got installed right in the first place!

---

### Post by kansasnoob on 2010-02-19
I'll bet you just ran those commands from the Live Desktop so that doesn't tell us anything. I just looked at your RESULTS.txt though (I know you've tried some things since then) and things look pretty wacky:

> => Windows is installed in the MBR of /dev/sda

That would make it appear that you should be able to boot Windows only, but I know you've made changes since then.

Things look really goofy here:

> sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  [B][COLOR="Red"]Grub 0.97 is installed in the boot sector of sda6 and 
                       looks at sector 353054022 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #6 for 
                       /boot/grub/menu.lst.[/COLOR][/B]
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   **[COLOR="Red"]/boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/COLOR]**


grub 0.97 is legacy grub but it's installed to the boot sector of a partition instead of to the mbr, but it can't work anyway because it has no menu.lst to read.

In other words this is a bloody mess :P

So hold on I'm going to type some very specific commands that must be copied-n-pasted. Just give me a little time.

---

### Post by kansasnoob on 2010-02-19
**[COLOR="Red"]Read this all before beginning![/COLOR]**

We're going to mount and chroot your Karmic install from the Live CD. You can read more about what I'm doing here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

But let's get to it:

```
sudo mount /dev/sda6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

Now run the following to be sure you are in Karmic:

```
lsb_release -a
```

If so:

```
dpkg-divert --local --rename --add /sbin/initctl
```

```
ln -s /bin/true /sbin/initctl
```

Now we need to update the package list: 

```
apt-get update
```

Now we start to fix it:

```
mv /boot/grub /boot/grub_backup
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub
```

```
apt-get --purge remove grub-common
```

```
apt-get install grub-pc
```

Note: if you encountered problems installing grub-pc (or it's dependencies, ie: grub-common) I'll need to see the output of "uname -m" and then I'll have to write some instructions for installing the packages using wget and dpkg.

```
update-grub
```

Wait for it to say done! Then:

```
grub-install /dev/sda
```

If that spits out any errors run:

```
grub-install --recheck /dev/sda
```

Now we'll exit and and unmount (remember I may need to see the output of "uname -m"):

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

Don't worry about errors after that last command because now you're going to reboot anyway.

Hopefully that does it. If not don't worry we still have options :)

---

### Post by kansasnoob on 2010-02-19
FYI regarding the "acpi=off" thing. If you try to boot and it fails and you think that might be the problem then from the Grub menu select your Ubuntu entry but instead of pressing Enter press e.

That will allow you to temporarily edit the boot command. For example your boot command might show:

```
linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=0b9e3325-9481-4227-ac76-910c64a904fe ro   quiet splash
```

You would just add acpi-off to the end and press Ctrl+X. Of course that's only a temporary change.

I'll have to do some studying about making that change permanent. You don't want to edit grub.cfg.

Edit: found the answer here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Look at the Grub 2 Files & Options section. It looks like the file to edit is "/etc/default/grub":

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
This line imports any entries to the end of the 'linux' line (Grub Legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". This line is where other instructions, such as "acpi=off" are placed.

---

### Post by ljupcho on 2010-02-19
ok, I have some changes. I have made it bootable, both ubuntu and windows. i think it's ok now.
I didn't do the commands from the big post you sent, instead i did this:
Based on the fact that it would boot with acpi=off, I first reinstalled ubuntu with that option checked with F6. I had it done like that the first time though.
Then, after installation I pressed "e" and added this "acpi=off" and ubuntu booted. I made this change permanent with running the  
sudo gedit /etc/default/grub as a root and made this change and save it.
Then I did the "update-grub" command that was executed successfully!  
I couldn't make this command work with the live CD, that was the part I had problems with, but now after fine boot i did it here.
I couldn't yet boot fine into ubuntu, so i put the live CD and did only the mount of the sda6 and the "grub-install --root-directory".
I restarted and boot to ubuntu fine. I can see as well that the change of "acpi=off" reflected to the grub.cfg file as well, nice :).
So far, I have no problems with booting ubuntu and windows.
I did the shell script and attached it. Can you please confirm that it looks good to you as well?

---

### Post by oldfred on 2010-02-19
OK, great that it now works. Sometimes we will spend days fixing things (partially becuase we want to understand what the problem is) when a clean install solves the problem pretty quickly.
If you have other issues do not hesitate to ask, just start a new thread with the issue.

---

### Post by kansasnoob on 2010-02-19
That looks OK, I would still like to see the output of:

```
grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4
```

Just to be on the safe side, so an update someday doesn't hose things :D

---

### Post by ljupcho on 2010-02-19
ljupcho@ljupcho:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)
ljupcho@ljupcho:~$ aptitude show grub|head -4
Package: grub
State: not installed
Version: 0.97-29ubuntu59
Priority: optional
ljupcho@ljupcho:~$ aptitude show grub-pc|head -4
Package: grub-pc
State: installed
Automatically installed: yes
Version: 1.97~beta4-1ubuntu3
ljupcho@ljupcho:~$ aptitude show grub-common|head -4
Package: grub-common
State: installed
Automatically installed: yes
Version: 1.97~beta4-1ubuntu3

that would be the output.
anyway, thank you for helping me, this forum looks very good. i will probably have more things to ask and solve eheh, so we'll keep in touch :)
cheers.

---

### Post by kansasnoob on 2010-02-19
That looks great!

---

