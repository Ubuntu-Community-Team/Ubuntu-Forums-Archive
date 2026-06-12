---
title: "boot from usb, led flickers then fails"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by Alan5 on 2011-03-31
I am trying to get Ubuntu to boot from a usb, and failing.

I have a two year old Acaer Aspire 5735Z with Windows Vista as the OS. This has USB as a possible boot source, now of course at the top of the list.

I downloaded 10.10 and installed on an empty 8 GB Kingston drive as guided. There is just under 4 GB on the drive. The drive had been used before and all deleted.

So at start up the first thing that happens is the led on the USB drive flickers for less than one second, and then the Windows boots.

How can I know that a boot sector is installed ?

Can someone please suggest a way forwards.

---

### Post by Dutch70 on 2011-03-31
How did you make the usb drive? 

You may need to check the md5sum of the downloaded .iso.
[[COLOR="RoyalBlue"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

Also check the integrity of the cd/usb.
[[COLOR="RoyalBlue"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

---

### Post by Hedgehog1 on 2011-03-31
> **Alan5 said:**
> I am trying to get Ubuntu to boot from a usb, and failing.
 
I have a two year old Acaer Aspire 5735Z with Windows Vista as the OS. This has USB as a possible boot source, now of course at the top of the list.
 
I downloaded 10.10 and installed on an empty 8 GB Kingston drive as guided. There is just under 4 GB on the drive. The drive had been used before and all deleted.
 
So at start up the first thing that happens is the led on the USB drive flickers for less than one second, and then the Windows boots.
 
How can I know that a boot sector is installed ?
 
Can someone please suggest a way forwards.
 
Just to be clear - you cannot copy the .iso to the USB stick.  You need to 'install' the .iso onto the USB stick
 
You can use this tool: [http://www.pendrivelinux.com/category/new-usb-linux-tutorials/](http://www.pendrivelinux.com/category/new-usb-linux-tutorials/)
 
Ot this link: [http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)
 
Once you have **installed **the .iso on the USB stick, the USB stick wil be capable of booting.
 
***The Hedge***
 
:KS

---

### Post by Alan5 on 2011-04-01
I am grateful to Dutch70 and Hedgehog1.

I loaded the stick using the installer provided following the download. Both download and installer finished with a job done message. I am sorry I did not record the details.

---

### Post by Dutch70 on 2011-04-01
Great, sounds good so far, let us know how everything goes.

---

### Post by Hedgehog1 on 2011-04-01
If your laptop has both USB 3.0 and USB 2.0 ports, at this time Ubuntu will not boot from USB 3.0 ports.  You can try a different USB port.

Otherwise there is very little here for us to work with.  All of our tools to help usually start with the sentence 'Boot from the LiveUSB and then...'

Do you have a different USB stick you can try this on?

Can you borrow a USB CD drive and install from a CD?

***The Hedge***

:KS

p.s. USB 3.0 ports work fine after the boot for extra drives; it is only booting from USB 3.0 that does not work yet.

---

### Post by EdwardR on 2011-04-01
When you first turn on the computer there is normally a key you can press that gets you into a boot menu (it's F12 on my Dell laptop) and from there you should be able to choose USB as the boot device.  You may need to first edit the BIOS to enable the boot menu.

---

### Post by Alan5 on 2011-04-01
My thanks to EdwardR for concern and help. But I did everything as instructed on the downlaod website, i used the installer.

Hedgehog1 says this is unusual, yes I could not find any reference by searching. I did not know, probably I did not notice, that USB 3.0 is not compatible. I will look into both sides of this as I understand that m/c and stick degrade themselves to match the lower of the two. The laptop has a cd/dvd drive, I will  make a cd, try that and report here in a day or so. I don't like walking away from a problem so I hope to see the usb working.

For background I understand that I have to convert from Windows to Linux. I have a legacy of files and equipment that I want to see working before putting MS in the fire.

My thanks again for all replies.

---

### Post by EdwardR on 2011-04-01
Not sure I understand you Alan5 - did you try pressing F12 a few times immediately after pressing the power button on your computer?  Did that take you to a boot options screen and you chose USB and it still didn't boot from the USB?

---

### Post by Hedgehog1 on 2011-04-02
> **Alan5 said:**
> Hedgehog1 says this is unusual, yes I could not find any reference by searching. I did not know, probably I did not notice, that USB 3.0 is not compatible. I will look into both sides of this as I understand that m/c and stick degrade themselves to match the lower of the two. The laptop has a cd/dvd drive, I will  make a cd, try that and report here in a day or so. I don't like walking away from a problem so I hope to see the usb working..

The issue is that USB 3.0 ports use a different (and much faster) 'driver' then the 2.0 ports.  The kernel carries the 2.0; but at least for 10.10 it does not yet carry the 3.0.  Given time it will.  We have also seen that CD/DVD drives that are connected to SATA-3 (6 gbs) ports will often not boot the LiveCD.  However, SATA-3 ports driving hard disks seem to work fine.

Most PCs not use SATA-3 for CD/DVD as SATA-2 is faster then they need, but a few forum members with home made systems have stumbled on this (*and reported it to the developers*).

We will see what the 11.04 kernels support very soon :D

***The Hedge***

:KS

---

### Post by Alan5 on 2011-04-02
Thanks EdwardR . Yes, it is F2 on the machine, and what is termed 'USB Key' was put at the top of the boot list. The proof that this was effective is that the USB stick twinkled for a short time at the start of the process.

And thanks Hedgehog1. I have done the necessary homework and now understand that USB 3.0 is a very different animal to USB 2.0 . I am sure that both elements are not 3.0 .

I have learned from this thread that the failure described is an unlikely original. That means that I have to repeat the entire process to be sure that no invisible accident occurred. I will also try CD booting to see what that does. I will report.

My thanks.

---

### Post by Alan5 on 2011-04-04
In summary :

1 i am a lazy, arrogant, impetuous fool.

2 Apart from that I am little further forward.

I repeated the usb stick load.. I prepared the same stick by deleting all therein in Windows, Then in a netbook with a Linux, using now, I found and deleted idlinux.sys .

I downloaded the iso. At the installation I discovered that I had made a blunder at the initial attempt because the installer works with two small windows, and I closed the parent window when its child had finished without reading the caution, or for that matter caring that the close butten was grey. Of course the parent had to continue working. So this time I got it right.

But the outcome is much the same.

At boot the usb led lit for a moment, then after a short delay, the Windows start screen appeared with the options of user. I wondered whether that might be intended by hijacking a bit of Windows to obtain the same control of users. Unlikely but possible. At the same time the C: was thrashing furiously and every 20 seconds the usb led would light briefly. I sat and watched for five minutes, then entered Windows. The disc activity stopped. Windows operated normally, seemingly at normal speed.

A usb  memory stick is a closed system as far as I am concerned, because I know that it is complex and dynamic. Wikipedia does not help. A hard drive is simple, based on fixed numbers. So as yet I don't understand how the boot works from the moving target in a usb. I will put a link here if I can find a good reference.

I have ordered a new 8 GB usb stick as all my sticks are used. Later this week I will report the result, then I fear that a failure will be the end of the line for this particular endeavour.

So, to the CD. And I feel like saying don't ask.

From the download page > Infra Recorder , then : iso burner software > NCH > download express burn for Windows . This was nothing like the process described. It does not start to install automatically and among the options offered there is no install button. So I quit. But NCH had installed a load of stuff on my machine, changed my homepage and given itself a toolbar in IE . I wonder if the Infra Recorder link has been hijacked.

My thanks to all who have got me here, a bit wiser and not yet finished.

---

### Post by EdwardR on 2011-04-06
Let's back up and let me give you some suggestions to try.  First off, I understand that you want to test drive Ubuntu on your Acer laptop to see if it runs well without having to mess with re-partitioning your hard drive and physically installing Ubuntu to your machine.  I also understand you have another computer, a netbook, with a version of Linux on it.  I've got two options you can try to install Ubuntu to a USB stick.

Option 1, using only your Acer machine:

Regarding the software to burn the iso file to a cd, it seems you might have been directed away from InfraRecorder and ended up with Express Burn instead.  These are two different software.  Express Burn may have a free trial period, but it will want to make you pay for it soon.  I expect it also made those other intrusive changes to your computer and web browser you mentioned.  You may want to uninstall Express Burn and use InfraRecorder instead.  InfraRecorder is a free software that will not attempt to take over your machine.

Go here to download InfraRecorder:
[http://infrarecorder.org/?page_id=5](http://infrarecorder.org/?page_id=5)

Don't click the links that are in the box directly below the InfraRecorder graphic at the top of the page, those are advertisements from Google and who knows where they take you.  Look down several lines to where you see:

All download options:

    * Installer (Windows 2000/XP/Vista/7, 3.90 MiB)

and click on the word Installer to download the program to install InfraRecorder.

Once InfraRecorder is installed, use it to burn the Ubuntu 10.10 iso file to a cd.

With the cd in the cd drive, restart the computer and press F2 and choose the option to boot from the cd drive.  This should start a live session of Ubuntu (it will take several minutes to load).  You could use this live session to test out Ubuntu, but it will run a bit slow since it will have to access files on the cd while it runs, and that is a slow operation.  What I recommend is that from here you create a live USB stick, which will both boot up faster and run faster than the live cd.  Another advantage with the USB is that you can create a "persistent" USB install that will remember configuration changes you make to the Ubuntu install (i.e. if you install a driver or save bookmarks in your web browser or make changes to your panels, then when you reboot the computer those changes will be remembered).

With the computer running Ubuntu from the live cd, do the following to install Ubuntu to the USB stick.
Plug the USB stick into the computer.
Run the program "Startup Disk Creator".
Under "Source disk image (.iso)" navigate to and choose your downloaded 10.10 iso file.
Under "Disk to use", choose your USB stick.  Make sure you have the correct device selected because the next step will erase everything on it.
Click on "Erase disk".
The next section will hopefully not be greyed out and will be selectable.  Under "When starting up from this disk, documents and settings will be", check the button for "Stored in reserved extra space" and move the slider over to the right.  I do not know if there is an upper limit to how many megabytes you can use here, if you want to be safe keep it about 1000 MB.  If you're feeling frisky, slide it all the way to the right.
Then click "Make startup disk".
When completed, close the program.
On your desktop, right click on the USB icon, click on unmount or eject and remove the USB stick.  Shut down the computer.  Plug the USB stick back in to the computer, start up the computer, use F2 to choose the USB boot option, and you should be good to go.

Sorry, I'm out of time to write up my second option.  Let us know if this works.

---

### Post by Alan5 on 2011-04-08
Many thanks EdwardR. I appreciate your care and detail.

I am on the point of repeating the attempt under Vista with a virgin usb stisk.

---

### Post by EdwardR on 2011-04-08
Please let us know how it turns out.  Good luck!

---

### Post by Alan5 on 2011-04-08
EdwardR many thanks.

InfraRecorder from SourceForge succeeds and I now boot Ubuntu from CD . It seems very nice.

I made a boot usb from System > Startup Disc Creator .  The usb contains 1.77 GB . It fails to boot, there are a few flickers from the led then Windows starts.

I think your help has been generous beyond any expectation.

OK, I can run Ubuntu in the machine. So I face the challenge of getting it to boot from a usb . This is desirable for reasons of pride as well as practice.

I infer that your option 2 is create a boot stick on my Aspire one . I will do that tomorrow. The stick should be universal .

I will try booting the AA1 with the usb already made, that will take two minutes after I post this.
 
I will report all progress and failure here.

---

### Post by Alan5 on 2011-04-08
With usb at the top of the boot list I shove the stick in the hole and switch on the Acer Aspire 1 . The response is :

     SYSLINUX 4.03 2010-10-22 EDD  Copyright (c) 1994-2010 H. Peter Anvin et al
     Error No configuration file found
      No DEFAULT or UI configuration directive found!
      boot:

I suspect this may be helpful.

I will tinker away and report.

---

### Post by oldfred on 2011-04-08
There were two different bugs with syslinux depending on what version. One just requires typing help and enter, the other requires editing the syslinux.cfg file and remove ui on a line.

syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

---

### Post by Alan5 on 2011-04-09
Thanks oldfred. It will take me some time to digest and benefit from your advice as I have so much to learn.

---

### Post by Alan5 on 2011-04-10
Can't make a boot stick under Linux.

Thinks : Who would want to do that ?

---

### Post by Alan5 on 2011-04-13
The second of oldfred's links advised that in the usb edit /syslinux/sislinux.cfg and delete the last line, which is : ui gfxboot bootlogo

I did this. It succeeded in the netbook and failed in the laptop.

In the laptop at boot the usb led gives three active pulses within a second and then Windows loads.

There is another problem further into the boot, because previously there had only been a single led pulse of light.
 

I will try harder. thanks oldfred .

---

### Post by Alan5 on 2011-04-20
I have followed oldfred's first link. There the team know they have a problem but are unable to define it, let alone localize the fault. Their best suggestion to boot from USB is to select help and then enter a carriage return.

I cannot get to the first screen of options so I can't select help, I am no further forward.

Many thanks for your thought, it was interesting.

---

