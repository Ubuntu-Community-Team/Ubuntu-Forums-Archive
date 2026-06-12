---
title: "Windows 7 dual-boot woes."
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by Quixotic Hacker on 2010-08-05
Yesterday I started trying to install Ubuntu because I'm interested in programming and the freedom Linux offers. First I tried downloading the iso, burning it to a DVD+R, and installing from there. I received the "no medium" error. I thought it might be due to which sata drive my cd/dvd player is plugged in, but incase it wasn't I tried the DVD iso. This also got the same "no medium" error. 

After that I thought that the problem was definitely with my CD drive, so I downloaded and installed Ubuntu with Wubi. This failed with the, "I can't find the installation.iso" error. I checked the location of the installation.iso and it was in the correct folder, so I followed its advice to run a "chkdsk /r". This didn't help anything. Finally I tried installing from a flash drive, but that ended in the same "no medium" error.

I checked my Bios and everything was running right, with it booting to the right cd drive and in the last case, thumb drive. Are there any solutions I can try? I really want to give Linux a shot? Would trying a different distro, help? Is there any way I can fix this without opening my box up and changing my CD drive to Primary Master?

Edit: I've been trying to install 10.04 btw.

---

### Post by oldfred on 2010-08-05
They do not recommend DVD's as they have to be written at faster speeds. I prefer flash drives. 

Also has link to USB Flash drive instructions:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Did you burn the ISO correctly not just copy it? If your look at the CD or USB it should show many files not just one xx.iso.

---

### Post by Quixotic Hacker on 2010-08-05
Thanks for the quick response.

For the CD and DVDs I used the default Windows 7 burner, which I think took care of it. For the flash drive I used the recommended flash drive software from the Ubuntu download page. I'm going to try and use a larger flash drive in the hopes that it might be a viable solution.

I'll try using a flash drive again and get back to you.

---

### Post by JBAlaska on 2010-08-05
> **Quixotic Hacker said:**
> 
I checked my Bios and everything was running right, with it booting to the right cd drive [COLOR="Red"]and in the last case, thumb drive[/COLOR]. Are there any solutions I can try? I really want to give Linux a shot? Would trying a different distro, help? Is there any way I can fix this without opening my box up and changing my CD drive to Primary Master?

Edit: I've been trying to install 10.04 btw.

The thumb drive and cd/dvd for that matter need to come before the HD in the boot order-as in CD, usb device, harddrive.

For burning software I highly recommend [ImgBurn](http://www.imgburn.com/). windows built in burning software is notoriously crappy. Remember to burn the iso as a image file.

---

### Post by Quixotic Hacker on 2010-08-05
Yeah. I set the order in the bios for the CD and thumb drive to come before the hard drive when booting. I thought maybe it was burning too fast so I'm trying some other software. If that doesn't work I'll give your suggestion a shot. Thanks for the help.

---

### Post by efflandt on 2010-08-05
Most of the Ubuntu isos are for CD's and I have never had any trouble writing CD-R's at any speed.  Although, my old PC has a problem with CD-RW (rarely successful), and until I got my new PC and did some research, I did not realize that few DVD's write successfully 100% of the time (it had frequent problems verifying backup DVD's).

If you can get the initial graphics at the bottom of the screen when Ubuntu CD or DVD boots, and press any key, there is a selection on that menu to check the disk you wrote.  Although, that may not help if there is some hardware issue recognizing your CD/DVD drive.

I think I used this software in Windows to check the readability by sector and files of a burned DVD (which can also check CD) [http://www.vso-software.fr/products/inspector/inspector.php](http://www.vso-software.fr/products/inspector/inspector.php)

---

### Post by Quixotic Hacker on 2010-08-05
Well, I can't find an empty flash drive so I'm trying a CD-R. I'm going to take your advice efflandt and verify the disc's legibility. Thanks for the assistance all. If I don't respond to this thread for 24 hours assume I've found a solution. In the mean time I'm going to check this periodically in case some people have new input.

---

### Post by JBAlaska on 2010-08-05
Good luck! You should definitely use [ImgBurn](http://www.imgburn.com/) to burn your iso, it's the very best free burning software for windows I've ever used, and I burn A LOT of cd's and DVD's

---

### Post by Quixotic Hacker on 2010-08-05
This "installation.iso" bug is giving me trouble. Every iso I've downloaded does not have the installation.iso in the install folder like the console wants. Is there any workaround? A way to download the installation.iso standalone? I'm trying 10.10 in case it's a mistake in the 64 bit version of 10.04. Any comments or solutions would be very helpful.

Thanks for the help thus far. The community itself has proven that Linux is worth it.

---

### Post by Quixotic Hacker on 2010-08-05
Trying 10.10 with a flash drive didn't work. If there any other suggestions they would be greatly appreciated. So far no progress. Even Wubi, my last resort, hasn't worked which is a big disappointment.

---

### Post by oldfred on 2010-08-05
What do you mean by installation.iso? If it is the 64 bit it should be:
ubuntu-10.04-desktop-amd64.iso

And what does not work with the USB flash drive?

---

### Post by Quixotic Hacker on 2010-08-06
If I try booting Ubuntu with Wubi, a CD, or a flashdrive I get an error that states it can't find the installation.iso in the ubunt/install folder. It gets that error halfway through, when it's installing after I boot to Ubuntu. If it isn't that error, it's an error about not finding the file medium. 

And now it won't even boot to the flash drive..

I'm getting someone who has decades more tech experience than I who might be able to figure out what is going on.

---

### Post by Quixotic Hacker on 2010-08-06
I've read up on Bitlocker and I think my PC is running it. Could that be causing all of these problems while trying to dual-boot? If so, how do I temporarily disable it?

Edit: Nevermind I don't have it activated.

---

### Post by YesWeCan on 2010-08-06
Wubi? Is it supported (properly tested) on Windows 7? The wubi-installer.org website doesn't list Windows 7.

Anyhow, I can confirm that there is absolutely nothing wrong with the 10.04 64-bit iso download.

Windows and linux aren't good bedfellows, which appears to be more the fault of Windows than linux. I wish the Ubuntu documentation was clearer about this; so many newcomers to Ubuntu get into all sorts of trouble. If you are new to this then I'd advise you to get a second hard disk and install Ubuntu on it. Keep the OS's separate. You can get Windows to create a blank partition on your Windows disk into which you can install Ubuntu but that is a little more prone to novice problems particularly in the boot loader area.

I switched from XP to Ubuntu about a year ago and there is no turning back. I have a computer again and it is mine. Now I keep Windows in various containment zones (which I like to call crèches :p); I have W7 64 installed on its own separate disk and I have installed W7 32 as a VirtualBox machine on my Ubuntu 10.04 64 host. VB has some limitations and performance drags, though. I have never used Wubi.

---

### Post by Quixotic Hacker on 2010-08-06
1. I tend to assume that everything that is compatible with Vista is compatible with Windows 7. There probably are programs that don't work, but I haven't found one up to this point.

2. I tried Wubi as a last resort after trying a Live CD, DVD, and flash drive.

3. I'm a novice when it comes to Linux, but not PCs in general. If partitioning will help I can try that. I was under the impression that partitioning was handled during the installation after it has booted up (which it fails to do for me). 

4. Unfortunately I can't afford a new hard disk, but I spent today making room on my current one.

5. My problem is that I can boot to Linux after a restart and it has the Ubuntu loading bar, etc...but before I can get it to install Ubuntu it gives me an error message that it can't find installation.iso, which to my knowledge doesn't even exist.

Thanks for the advice, friend. I'll try partitioning and putting my ubuntu install there and see if that works.

---

### Post by oldfred on 2010-08-06
Were the drive(s) you have ever in RAID? Some BIOS set raid as standard even if you only have one drive. the RAID metadate can cause problems.

Have you tried using the alternate installer. It uses command line so graphic issues are minimized.
[https://help.ubuntu.com/10.04/installation-guide/](https://help.ubuntu.com/10.04/installation-guide/)

---

### Post by Quixotic Hacker on 2010-08-06
I tried Unetbootin and it gave me the "Unable to find medium containing live file" error message in Busybox. I've freed up space for a Ubuntu partition (27 GBs of unallocated space) and pointed it to the right iso. I don't understand. I've googled the error, but nobody seems to have found a solution for it besides changing a disc drive from SATA to IDE (I don't have any IDE cables, just SATA) and Unetbootin bypasses the need for a disc drive anyways.

@Oldfred: I'm not running RAID.

Thanks to everyone for bearing with me. This process is becoming unbearable for me however.

---

### Post by Mahngiel on 2010-08-06
Did you check the md5sum before burning? Perhaps your download was bad?

---

### Post by Quixotic Hacker on 2010-08-06
I've tried multiple isos, so I doubt it, but I'll give it a shot.

---

### Post by Quixotic Hacker on 2010-08-06
Just ran md5sum and the iso is fine.

---

### Post by oldfred on 2010-08-06
Normally we ask you to run this when you have trouble booting Ubuntu. But maybe it will show something. Use a liveCD and download this script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Quixotic Hacker on 2010-08-07
Unfortunately I can't access the terminal on Linux. I get stuck in the shell before I get that far. I tried an installation of Arch and ran into similar problems there.

---

### Post by JBAlaska on 2010-08-07
> **Quixotic Hacker said:**
> I tried Unetbootin and it gave me the "Unable to find medium containing live file" error message in Busybox. [COLOR="Blue"]I've freed up space for a Ubuntu partition (27 GBs of unallocated space) and pointed it to the right iso.[/COLOR] I don't understand. I've googled the error, but nobody seems to have found a solution for it besides changing a disc drive from SATA to IDE (I don't have any IDE cables, just SATA) and Unetbootin bypasses the need for a disc drive anyways.

@Oldfred: I'm not running RAID.

Thanks to everyone for bearing with me. This process is becoming unbearable for me however.

[COLOR="Blue"]1[/COLOR] I think we (unless I'm the only one confused), need to find out exactly the steps your taking to burn the image to cd then try to install Ubuntu 10.04.

"pointing the iso" at a un-partitioned space on a HD? I can't quite understand what you mean by this.

I tried following the thread, but I think one or both of us are confused. So please bear with me and I'll try to help.

1-Are you able at this time to boot from a CD?
2-did you download the ubuntu-10.04-desktop-amd64.iso and burn it to a CD using a **Image burning mode and not as a data file?**
If both those answers are yes, please follow this illustrated guide: [Installation CD Integrity Check](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

Pay special attention to this part:

[B]Verifying the CD/DVD Integrity
1. Insert your Ubuntu CD into the drive of the computer that you want to run/install Ubuntu onto.
2. Turn the computer on, or restart the computer.[/B]
**3. While booting from the CD,** [COLOR="Red"]hold any key to access the CD menu.[/COLOR]
**4. At the CD menu, choose 'Check CD for Defects'**

Wait for this process to complete and it will let you know if all of the files are 100% intact. 

If they are, reboot the computer with the Verified disk in the drive and please report exactly what happens after that.

[B]If you get to the part where the install asks you where you want to install Ubuntu, BE very careful how you answer if you want to put Ubuntu in the unallocated free space on your HD (Which I think you want to do).
[/B]
The option you should normally choose if all is as described  above, and you do have 27GB of unallocated space on your HD is "install to largest available free space"

*At this point I have to say I have not tried that option since Feisty beta, and it installed to my primary windows partition. I'm sure that has been fixed long ago, but since then I have been doing a manual partition. Maybe it would be better to report back here at that point for guidance.*

If you know all of the above and I missed the point, I apologize, but if you google "can't find installation.iso ubuntu" you'll see it just does not happen unless you tried to extract the ISO to your HD to try to install it from there. If that's the case you missed some steps.

I hope this doesn't confuse you further, and I'll try to check back to answer as best I can,
Good Luck

---

### Post by Quixotic Hacker on 2010-08-07
I spent last night checking the CDs and found no defects. I also did the MD5checksum and no discs have problems. 

I'm sorry for being unclear. I've tried this process several times using different methods and each one hasn't worked, so my thoughts are a bit all over the place. 

I've been trying to research this "unable to find a medium containing a live file system" error. This error brings me to the intramfs shell. There are several people that have run into this problem, but there is no definite solution. Some have tried erroneous solutions involving their disc drives (changing a SATA cable that runs 6 Gbs to a 3Gbs cable) and that seems to have resolved it for them, but those solutions have not worked for me. 

The problem is not due to a corrupt download, nor a disc being improperly burned. I wish I knew how to proceed, but none of the threads I've researched have solutions that work.

Sorry for not being clear and thanks for sticking with me.

---

### Post by YesWeCan on 2010-08-07
> **Quixotic Hacker said:**
> 1. I tend to assume that everything that is compatible with Vista is compatible with Windows 7. There probably are programs that don't work, but I haven't found one up to this point.

2. I tried Wubi as a last resort after trying a Live CD, DVD, and flash drive.

3. I'm a novice when it comes to Linux, but not PCs in general. If partitioning will help I can try that. I was under the impression that partitioning was handled during the installation after it has booted up (which it fails to do for me). 

4. Unfortunately I can't afford a new hard disk, but I spent today making room on my current one.

5. My problem is that I can boot to Linux after a restart and it has the Ubuntu loading bar, etc...but before I can get it to install Ubuntu it gives me an error message that it can't find installation.iso, which to my knowledge doesn't even exist.

Thanks for the advice, friend. I'll try partitioning and putting my ubuntu install there and see if that works.
Let me make sure I understand what you are describing. There are many different stages here. Are you installing 32-bit 10.0.4 or 64-bit?

1) Can you can boot your PC off a Ubuntu "live" CD (that's the default download on the Ubuntu download page)? That is to say, can you can run the OS off the CD without installing it first? This is an important milestone.

2) If 1 ok, what happens when you try to install using the live CD? What stages appear to work ok? Do you get to the partitioner and can you select the new partition you created using Windows?

3) After it starts installing how far does it get? Does it ask you to reboot? What happens after it reboots...what do you see before you get the installation.iso error.

---

### Post by Quixotic Hacker on 2010-08-07
Ignore the installation.iso. That was only a problem in Wubi, which I'm not going to use any more because frankly if it isn't working I might as well get a Live CD to work. I've been trying to install 64-bit.

1. I cannot boot to the Live CD and run Ubuntu. I start the booting process and get stuck on the initramfs shell. Once there it gives me an error saying "Cannot find a medium containing a live file system."
2. I don't get to the installer within the Live CD.
3. N/A

Thanks for helping to get to the bottom of this issue. It truly is reassuring to know that everyday people help people with these sort of issues, despite not being paid.

---

### Post by oldfred on 2010-08-07
IS your CD rom set as slave? Then it could be this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543875](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543875)

---

### Post by Quixotic Hacker on 2010-08-08
I don't use IDE. Both my hard drive and CD drive are SATA.

---

### Post by YesWeCan on 2010-08-08
> **Quixotic Hacker said:**
> Ignore the installation.iso. That was only a problem in Wubi, which I'm not going to use any more because frankly if it isn't working I might as well get a Live CD to work. I've been trying to install 64-bit.

1. I cannot boot to the Live CD and run Ubuntu. I start the booting process and get stuck on the initramfs shell. Once there it gives me an error saying "Cannot find a medium containing a live file system."
2. I don't get to the installer within the Live CD.
3. N/A

Thanks for helping to get to the bottom of this issue. It truly is reassuring to know that everyday people help people with these sort of issues, despite not being paid.

I presume when you boot off the live CD you get the language selection screen, then the main menu screen with options like install, check media, memory test. Is that right? Then when you select boot from CD there is some pause (how long?) and presumably a lot of text on the screen and then it stops at a shell prompt.

Can you run the check media facility ok?
Can you run the memory test ok?

I'm no expert (you get what you pay for around here :p ) but it sounds like the ram disk program cannot read the CD. What is your Motherboard? If you have a choice of SATA 2 or 3 make sure the CD is in a SATA 2. Does the CD have PATA/IDE as well - can you try that? Make sure your bios settings are appropriate for your CD.

Lastly, it usually takes an army to prevent Knoppix from booting. Try burning a live Knoppix CD and booting it: [http://www.knoppix.org](http://www.knoppix.org)

edit: I just noticed there are an impossible number of downloadable versions on the mirrors. You probably want: KNOPPIX_V6.2.1CD-2010-01-31-EN.iso.

---

### Post by oldfred on 2010-08-08
Have you tried the f4 safe graphics mode?

Another setting to try:
all_generic_ide

---

### Post by Quixotic Hacker on 2010-08-08
[SIZE=4][COLOR=Red][B]Huge update!
[/B][/COLOR][/SIZE]
So I've resolved the problem folks thanks to a little help from a knowledge base.

I have a motherboard (nForce 750a sli) that doesn't play nice with Linux (Linux won't recognize the SATA drives on it) and requires an added command to make it work. Adding pci=nomsi to the end of the boot options when installing and removing the "no splash" command worked! I'm not sure if this will help everyone with the "Unable to find a medium containing a live file system" error, but it's worth a shot.

For full details on compatibility errors with the 750a SLI check out [https://answers.launchpad.net/ubuntu/+question/57856](https://answers.launchpad.net/ubuntu/+question/57856) and scroll down to GrumpyOldGoat's post.

Thanks for all the assistance, it has kept me going all this time.

With that--requesting lock.

P.S. I'm proud to say that I wrote this while on Ubuntu.

---

### Post by YesWeCan on 2010-08-09
\\:D/ Well done.

---

