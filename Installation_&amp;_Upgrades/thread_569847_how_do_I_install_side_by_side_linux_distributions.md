---
title: "how do I install side by side linux distributions?"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by mactece on 2007-10-07
I want to be able to instal and mess about with other distributions - to see what they are like and because I have some older hardware which I'd like to set up for the kids but will need a minimalist distribution to run. I'd also like to be able to experiment with ubuntu without messing up my main system and also be able to give new versions a go before deciding to upgrade.

I've set up my hard drive with 4 partitions:

1. Ubuntu operating system - approx 20Gb
2. Swap File (2Gb?)
3. Home - approx 200Gb
4. Unused - approx 20Gb

I'm hoping that  I can install other distros in the unused area and point them to the Home partition and set Grub to give me the choice of distros at boot. 

Am I right? If I am is it as straightforward as I describe? How do I edit the GRUB?

Any thoughts, contributions, solutions or answers gratefully received. I've had a good trawl though the forums and I don't think anyone has addressed this question directly before so it would be useful to have a thread to answer it.

Many thanks

David

---

### Post by forestpixie on 2007-10-07
It's not any different than dual booting with windows - although from what I've read here it's probably not such a good idea to share /home, but that's just an observation.

---

### Post by kirios on 2007-10-07
[COLOR="DarkRed"]Run the following command to check the name of the unused partition: 
```
sudo fdisk -l 
``` 
For example, if you have a single hard disk and the unused partition is the fourth primary partition, fdisk will identify it as hda4 which is (hd0,3) for grub. 
Install the second distro to the unused partition but make sure it installs grub to the same (root) partition rather than to the MBR.
Boot into Ubuntu, press Alt-F2 and type: 
```
gksudo gedit /boot/grub/menu.lst 
```
Add the following lines to the menu.lst file: 
```
Title [name of the second distro] 
rootnoverify [name of the previously unused partition, e.g. (hd0,3)] 
chainloader +1
```
Run the following command in a terminal: 
```
sudo update-grub
```
When you reboot, grub will have a new entry for your second distro.[/COLOR]

---

### Post by mactece on 2007-10-09
Thanks for your comments and help.

I tried to install PCLinux on the spare partition (partly because I'm having trouble with mplayer and I've read that their implementation may be better) and followed your suggestions as best I could. Unfortunately the PCLinux installer seems to have moved GRUB onto its partition so the Ubuntu version I editted is not being seen. Still if you don't break it you can't fix it. PCLinux install wanted a kernel number for Ubuntu which I didn't have and also didn't worry about because I didn't realise it would move control to its partition.

I've found a utility called super grub which claims it can restore order to things. So I'll try that. Any other suggestions are very welcome.

Picking up on the comment that I shouldn't share the home directories, I think this is probably good advice. As things stand both OSes are sharing the same home directories because that's where all my data and files are. I need to move the home directories onto each OS's individual partition and leave the data in the large partition to be shared, I think. Presumably this means changing the mount points and copying data around. Can anyone help with this so I don't have to do a complete reinstall? The data is backed up on an external hard drive. The operating model for this setup is that Ubuntu is my main OS and the others are for learning and experimenting.

Again, many thanks,

David

---

### Post by forestpixie on 2007-10-09
> Supergrub...So I'll try that

that should sort you out, I used it to sort my boot out 

have a look at [psycocats]("http://www.psychocats.net/ubuntu/separatehome") for moving your /home directory - it's quite simply put and has helped me more than once

good luck and glad you're more or less sorted out

when you're finished and ready can you make sure you mark thread solved - makes it easier for people searching if they know there's a solution :)

---

### Post by Herman on 2007-10-09
Hello mactece,
I agree with what forestpixie and kirios have already advised you. 

In order to be able to chainload Ubuntu, you will need to install the IPL for GRUB to the first sector of your Ubuntu partition.Here's a link about how to install GRUB anywhere you might want, [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") eg; with Live CD.
Chainloading is a useful way to multiboot because you can chainload not only another GRUB, but also LiLo can be chainloaded, (some other Linuxes use LiLo by default instead of GRUB), or Windows NTLDR can be chainloaded.

If you are booting another Linux that does use GRUB, another kind of GRUB entry that's easier is the 'configfile' boot entry, where you get GRUB to bring up the other Linux by its /boot/grub/menu.lst file or grub.conf file or whatever it has.
You don't need to have GRUB's IPL installed anywhere special at all for that.

A third way of avoiding a direct kernel boot is to boot the other system by its symlinks to the kernel and initrd.

You can boot another operating system directly by the kernel itself but if you do that you will need to keep updating GRUB manually every time the other operating systems have a kernel update. It might not be a problem if they are only installed for a short time though.

Here's a link if you want more details about what I just typed about, [Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")



About partitioning, I always prefer installing in one '/' (root) partition per operating system, I never bother messing around with /home partitions, I personally just don't think it's necessary. I know there are lots of other people who think it's a good idea though. 
For multi booting, it's too messy for me I think. (Just my personal opinion).
forestpixie's link to aysiu's site should help you there I hope. I'll take another look after I get a little sleep and see if you still need help with that. If you need specific help please post a copy of the output form 'sudo fdisk -lu'
```
sudo fdisk -lu
``` and a copy of your /etc/fstab
```
sudo gedit /etc/fstab
```and '[COLOR=#000000][FONT=Bitstream Vera Sans Mono]ls /dev/disk/by-uuid/ -alh'
[/FONT][/COLOR]```
ls /dev/disk/by-uuid/ -alh
```I can help you if I have all that information and a breif explanation of which partition is which. :)

It's okay to let all your Linuxes share the same swap area as long as you don't use 'hibernate' mode. I usually let mine all share the same swap area.

I just updated my article on editing /etc/fstab here if it will be any help to you at all,[ Mount a different Linux filesystem (ext3) in Ubuntu]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu")

See how you go, I'll be back in a while to check,
Regards, Herman

---

### Post by mactece on 2007-10-09
Thanks for all your help and comments - I could never have sorted this by myself. I need to find some time to try all these things on my home pc (I'm posting from work, just now) so will have a play this evening when I'm home (wife and kids permitting) and probably post again tomorrow.

Regards

David

---

### Post by mactece on 2007-10-10
I downloaded supergrub and made a disk which succesfully restored control to the Ubuntu partition.  
It was not as intuitive as I had hoped and I don't have dual boot yet.

Plan of action
- read all your posts again and make sure I understand them.
- read the manual for supergrub so that if I have another boot problem I'm not just guessing when I fix it!
- reinstall pclinux in one \ directory. Then get it to mount my main partition (the one that ubuntu thinks is HOME) as a storage directory. Then PCLinux will not mess about with the settings for my existing setup but will be able to get to my files which means I can have a proper play without ruining my existing setup.
- use supergrub to setup/fix the boot options correctly this time.

I'll post again when I've done all that which is likely to be at the weekend, now.

By the way ...

PCLinux did install very nicely but doesn't recognise my usb keyboard at boot (only once it is fully loaded); will need far more tweaking than Ubuntu did to get it going properly; is not as intuitive as Ubuntu. So I may choose another OS - my main reason for starting this was to look at light installations for a low tech pc for my kids (5 and 4) to use.

I wanted to look at PCLinux because of the problems I was having with mplayer. I came across a front end for mplayer, called smplayer, which I've installed in Ubuntu. It works very nicely, is quite nice to look at and also remembers where you pressed stop and restarts playing from that point. The slider control for moving through films works properly, too!

Regards

David

---

### Post by kirios on 2007-10-10
[COLOR="DarkRed"]When you install your second distro (PCLOS or other), install the bootloader to the same partition as the / filesystem so that it doesn't overwrite the Ubuntu bootloader (if it's still on the MBR). 
Then, boot into Ubuntu and chainload the second distro as described earlier.[/COLOR] 
 
> **mactece said:**
> Plan of action
- read all your posts again and make sure I understand them.
- read the manual for supergrub so that if I have another boot problem I'm not just guessing when I fix it!
- reinstall pclinux in one \ directory. Then get it to mount my main partition (the one that ubuntu thinks is HOME) as a storage directory. Then PCLinux will not mess about with the settings for my existing setup but will be able to get to my files which means I can have a proper play without ruining my existing setup.
- use supergrub to setup/fix the boot options correctly this time. 

> **mactece said:**
>  ...my main reason for starting this was to look at light installations for a low tech pc for my kids (5 and 4) to use. 
[COLOR="DarkRed"]I haven't tried Edubuntu but it sounds interesting. [/COLOR]

---

### Post by mactece on 2008-02-15
I didn't post on this for a while. Sorry - events overtook me and this project has only been pursued intermittently Some reflections:

- I had originally set out to create a kind of "How to" thread for running side by side distributions. This proved unnecessary as the excellent and talented people who responded had already created the necessary information. I hope the links in this thread prove useful if you come searching here.

- If you are going to go this way then burn a copy of supergrub first. 

- The idea of having each distro and the data on separate partitions seems to be a robust one and has allowed me to be flexible in how I use my PC. It has meant that adding and scrubbing distros has been (relatively) easy and my data could be used by both so that I could do meaningful comparisons.

- When you install a second distro it will try to take control. You need supergrub, some luck and a bit of common sense during the installation to deal with this. Usually the consequence is that GRUB is written over or a different partition is pointed at and so GRUB needs resetting. (See threads above for more)

- You will need to make decisions which can seem system threatening (they probably aren't) but I was able to make these with confidence because I had prepared. So, backup your data and be prepared to reinstall everything. I have an external disk which is bigger than my hard drive so I simply copy everything across. If I have to reinstall then I set the partitions up as before and simply copy everything back (this is slightly harder than it sounds as I also have other family members' data to do as well - I manage the process as SU and then reset the permissions after). DON'T PANIC - this didn't happen during this project but has happened with some of my wilder ideas.

- This has been a great way to find out about other distros properly - using a disk is too slow and unrealistic. As a result I have changed the way my desktop is set up and installed KDE alongside GNOME (although I still use GNOME as the desktop) and use a lot more KDE packages which I don't think I would have played with otherwise. Overall I'm still using UBUNTU and I'm happy I'm not missing out. In the end I'm back to one distro but with lots of improvements.

---

### Post by housam on 2008-02-15
I've win-xp , ubuntu Feisty and Gutsy on my laptop. all are working perfectly without editing Grub.
Do you think I'll need to edit Grub if I decided to install KDE?

---

### Post by Herman on 2008-02-15
:) Hello housam,
It's not compulsory to edit GRUB, Ubuntu or Kubuntu or whatever you install next will detect the existing installations for you and create a new GRUB menu.lst file for you with direct kernel boot entries for the other *buntus in it automatically.
The last *buntu you install will install it's GRUB to MBR for you.
 
You can probably get away with booting from those direct boot entries for quite some time.
You should be aware though, that only the boot entries for the operating system that the menu.lst file belongs to will be updated when a new kernel is installed in an update.
That means you may install new kernels in your other systems booted from that  GRUB menu but you will still be booting them by their old kernels.
You can keep on booting the old kernels if you want.

Kernel developers work hard to supply us with new improved kernels for some reason though. Usually the new kernel is worth using, it improves the operating system in some way and it's a good idea to update whenever we can.
The old kernels remain in the operating system for a long time and we can still keep on booting them if we want.

You can update your direct kernel boot entries manually for your other installed *buntu's or not, it's up to you.
I like to be booting the latest kernels. However, I'm very lazy and I like to make the computer do the work for me whenever I can. That's why I think it's worth the little extra work of changing from direct kernel boot entries to configfile or chainloader entries pretty soon after I finish the latest installation. 
It only needs to be done once, for the last operating system we install or for whichever one we want to have in MBR and use as our main boot manager.
Then after that, each operating system will be booting by its own GRUB menu, which will be kept up to date automagically.

I'd say if you're not sure about it, (if you can't understand what I'm talking about), don't worry about it, just add you extra operating systems and have fun. 
If you can understand what I mean then it's probably worth it if you're going to keep you installations for long. It depends on what you use your operating systems for and how fussy you want to be and how lazy you are, :)

Regards, Herman :)

---

### Post by Herman on 2008-02-15
>  Do you think I'll need to edit Grub if I decided to install KDE?
:oops: ... er, did you mean you are think of installing Kubuntu, as another operating system? 
Or did you mean you want to install kubuntu-desktop in one of your Ubuntu systems?
If you are just installing kubuntu-desktop it won't affect GRUB at all.

---

### Post by housam on 2008-02-17
> **Herman said:**
> :oops: ... er, did you mean you are think of installing Kubuntu, as another operating system? 
Or did you mean you want to install kubuntu-desktop in one of your Ubuntu systems?
If you are just installing kubuntu-desktop it won't affect GRUB at all.

I mean I'm gonna install Kubuntu Gutsy as a replacement of ubuntu Feisty.( I already have win-xp , ubuntu Feisty & Gutsy on my laptop ).

---

### Post by Herman on 2008-02-17
> I mean I'm gonna install Kubuntu Gutsy as a replacement of ubuntu Feisty.( I already have win-xp , ubuntu Feisty & Gutsy on my laptop ). :)   Oh, okay, cool! It sounds like you do things very similar to the way I do then.
I also had WinXP and Feisty and Gutsy in my laptop, but I installed Hardy Herron over my old Feisty installation.

I'm not sure if you'll be interested or not, but this morning I invested a little time in this other thread                                                                                                              [dual boot gutsy/hardy]("http://ubuntuforums.org/showthread.php?t=637847")
 in which I put some more information about dual or multiple booting with more than one Linux.
Regards, Herman  :)

---

### Post by housam on 2008-02-17
Thanks for the informations, but I only install a final release versions because I've valuable data on my laptop and I don't want to lose it in case something happened with a test version. 
B.Regards
Housam

---

### Post by Herman on 2008-02-17
:) Sorry, no, I didn't mean to imply you should install Hardy, what I meant was there are some posts there I made about how to use GRUB when we're have more than one installation of Ubuntu or other *buntu in the same computer.

Regards, Herman :)

---

### Post by housam on 2008-02-17
> **Herman said:**
> :) Sorry, no, I didn't mean to imply you should install Hardy, what I meant was there are some posts there I made about how to use GRUB when we're have more than one installation of Ubuntu or other *buntu in the same computer.

Regards, Herman :)

I've read your posts , it is great. and I think that when the final kubuntu hardy is ready to be installed, the grub menu will be generated automatically having all OS's as done before when installing other distros of ubuntu. 

B.regards
Housam

---

