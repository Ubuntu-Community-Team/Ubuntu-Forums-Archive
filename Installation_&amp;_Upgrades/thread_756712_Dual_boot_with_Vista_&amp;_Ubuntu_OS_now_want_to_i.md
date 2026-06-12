---
title: "Dual boot with Vista &amp; Ubuntu OS now want to install XP"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by julyderek on 2008-04-16
Hi,

I dual booted Ubuntu (Gutsy Gibons) on my Vista Lenovo 3000 N100 laptop with Grub and Ubuntu.

I now want to install WinXp in the Ubuntu partition by overwriting it.  Will I have to remove Grub ?

How do I do that?  If I want to install Ubuntu back over XP will I be able to do that?

Thanks in advance.

Regards,
Derek

---

### Post by Nopposan on 2008-04-16
Well, I've never done this, but from what I have experienced installing Windows XP after Ubuntu, I'd say you'd better roll up your sleeves and prepare a nice hot pot of coffee.

I don't think you have to uninstall grub, but you'll probably have to add Windows to the list of systems that grub will display for boot selection.

There are tutorials about how to install XP; I remember, 'cause I used one.  Ugh!  I have to wrap up this message very quickly though.  'Sorry, I don't have time to Google right now.

What you need to do is you need to repartition your hard drive.  I remember I used gparted to create some empty space on my hard drive for WinXP to use.  Maybe I even formatted it as NTFS first, but I don't remember.  Then, I just ran the graphical installer from the Windows install CD and selected the correct partition to install to.  (I really wish I could dump Windows altogether though; had to use Filemaker Pro for work.)

Vista, well all I know is it's really slow even on moderately stoked computers.  'Can't help with Vista at all.  'Sorry.  But I assume it still uses NTFS, and I hope for your sake that Windows XP won't somehow be incompatible on the same hard drive.  That would be for a Windows forum though.

Peace.

---

### Post by NightwishFan on 2008-04-16
You need of course a free partition for the install, as the above said. If you install Xp, I believe it will use Windows boot loader which may ignore Ubuntu if it is installed (but not remove it so it is ok) I think after you do that you can use the super grub disk or the ubuntu live cd and restore grub. You can likely find a method for that somewhere on the forums with the search function.

---

### Post by julyderek on 2008-04-17
Thanks guys.

What if I remove Ubuntu & Grub and then start over ?  Is that possible ?

Windows Vista is the worst operating system I have used.  I have used all of Windows from 3.1 to 98 to ME to 2000 to...... and Vista is rubbish.

The only reason I am removing Ubuntu is that for Internet access I have a local provider with Huawei EC321 card for which there is no known Ubuntu drivers :(

Thanks again.

---

### Post by benali72 on 2008-04-17
If you have Vista and you're trying now to install XP, native Microsoft software without any additional tools will not do the job.   If you want to install multiple MS operating systems on one computer, you need third party tools,  

One solution is a commercial product like System Commander.  It will easily allow you to install multiple Microsoft OS's, protecting each install from the other(s), allowing you to partition the disk, and providing a Grub-like boot selection menu.

Another solution is free -- use Ubuntu or other Linux on a Live CD to perform operations like protection and copying of the boot record (MBR), partitioning, and Grub menu for OS selection at boot time.

The Linux route is free but you'll have to have a pretty good understanding of the steps you need to perform, whereas a tool like Systems Commander or its competitors costs but requires less expertise.

Best of luck.

---

### Post by Nopposan on 2008-04-22
julyderek said:> Thanks guys.

What if I remove Ubuntu & Grub and then start over ? Is that possible ?

Windows Vista is the worst operating system I have used. I have used all of Windows from 3.1 to 98 to ME to 2000 to...... and Vista is rubbish.

The only reason I am removing Ubuntu is that for Internet access I have a local provider with Huawei EC321 card for which there is no known Ubuntu drivers

Thanks again.

Yes, of course it's possible.  The best way to start over though, IMHO, is to copy any important files to another disk and then wipe out your whole hard drive before you start over.

No kidding.  Why?  'Cause sometimes the old data that's on your system can interfere with a new install, particularly when that new install is of something that you installed before in the same way.  I'd say, minimally, you should use gparted or some other tool to reformat the hard drive.  But I find erasing hard drives to be a lot of fun.  'Makes me feel POWERFUL when I remind myself how people all over the place fret about not being able to get rid of the sensitive files on their hard drives, etc.

It's so easy!  First, boot up your Ubuntu Live CD.  Then, you just open a terminal emulator, go to a root prompt with the command ```
$ sudo su
```.

Then ```
# shred -fv /dev/sda1
```
or ```
shred -fv /dev/hda
```
for whichever hard drive you wish to whipe clean.

Shred is a really cool software that writes 000000 then 1111111 and then 0100101010101001000101010010010101111001011010101010101010110000101010101011110011010
to your hard drive.  Many many times.  This doesn't just slate the files to be overwritten like "deleting" them or "rm" does; it attempts to, and eventually does, obliterate them.  If you allow shred to work long enough on your hard drive, the data will be impossible for even forensic experts and high-tech identy thieves to recover.  Hahahhahhhahahahhahahah!

Just one caveat, it may take many hours for shred to finish the job.  The verbose option allows you to monitor the progress and you can just type Ctrl C to halt the software if you get tired of waiting.  For your purposes, it's o.k. to just give one or two passes.  I think the code for that would be something like:```
# shred -fv n 2 /dev/hda
``` but read the man pages for shred.  It's soooo cool!

Then, when you want to start over, just start off first with installing Windows XP and use Ubuntu's installer, which includes NTFS shrinking capabilities, to install Ubuntu.  You don't really want to install MS-Vista, do you??  Did you know that there are all kinds of disguises for XP to improve its look and feel?  Many of these XP tweaks are open source solutions, so check out sourceforge.  My understanding is that Vista has security improvements, but Windows probably won't be your primary OS anyhow, so just use some good antivirus software on XP with the latest updates and it will be fine for occasional use.

Oops, you have an incompatible wireless card?  Oh.  Well, security will still probably be fine on XP if you're careful not to install questionable software and you don't use IE.  Are you sure there's no solution for your wireless card?  Are you sure you can't use any other wireless card?  That sucks.  No, excuse me, THAT REALLY BITES!

Oh well.

Cheers!

---

