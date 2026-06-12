---
title: "Installing Windows on Ubuntu"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by evolushun on 2007-09-30
OK...so, first of all, I have worked on Linux for exactly 15-18 hours now.  I am tired of Microsoft.  As a long time user, obviously I have developed some necessities with some programs from Microsoft.   I have installed WINE and tried to install Mixmeister but to no avail.   I have done my research ladies and gentleman and the final ruling is that I need to have an XP as well.  I am running on Ubuntu right now and I hate to say this, but since I am learning as much as I can on my own, can someone take the time to break it down for me in Lehman's terms how I accomplish this?  I have an external HDD that I absolutely have to make sure does not get erased.  I am pretty much open to all suggestions as long as I can get a basic tutorial on how to get there.  Thank you in advance for any help and thank you all for creating this amazing OS.

evolushun

---

### Post by AnRa on 2007-09-30
You may try using [VirtualBox](http://www.virtualbox.org/).

---

### Post by evolushun on 2007-10-01
> **AnRa said:**
> You may try using [VirtualBox](http://www.virtualbox.org/).

LOL...ok, but remember...I am a complete moron when it comes to Ubuntu and am looking for some guidance on what to do and how to do it.  Linking me to a site is great, because in my searching, I haven't found a program that does this but linking me does not show me what to do.  I am the type of person that if you guide me on how to do something one time, I get it and understand it.  If I have to read how to do it, it goes in one eye and out the door.  I know I sound like I'm whining but this is the only problem I cannot fix and it's the only thing making me miss XP.  I just hope that someone here is drooling at the fact of getting another faithful user from Microsoft and wants to lend a helping hand.  I need to get this fixed within a few days due to certain projects needing fixed by that deadline.  Thank you again.

evolushun

---

### Post by ddrplayer512 on 2007-10-01
> **evolushun said:**
> LOL...ok, but remember...I am a complete moron when it comes to Ubuntu and am looking for some guidance on what to do and how to do it.  Linking me to a site is great, because in my searching, I haven't found a program that does this but linking me does not show me what to do.  I am the type of person that if you guide me on how to do something one time, I get it and understand it.  If I have to read how to do it, it goes in one eye and out the door.  I know I sound like I'm whining but this is the only problem I cannot fix and it's the only thing making me miss XP.  I just hope that someone here is drooling at the fact of getting another faithful user from Microsoft and wants to lend a helping hand.  I need to get this fixed within a few days due to certain projects needing fixed by that deadline.  Thank you again.

evolushun

VirtualBox is a program that lets you use something called "virtual machines." You've probably heard about people running Windows inside a Mac, right? Well, the same exact thing, but in Ubuntu. Now, another product you can use is VMWare, but I never used it for Windows. Now I now how you feel, because I have to use iTunes for my iPod (I like to buy music online and the alternatives don't cut it for me) and Office 2003 (I like Office).

Now here's how I installed VirtualBox:

**Now, even though it looks long for you, I take you from no VirtualBox to a Full Windows XP Virtual Machine. I worked REALLY Hard to type this for you so read it and follow it.**

I am assuming you are using Ubuntu 7.04.

I went
[URL="http://howto.landure.fr/gnu-linux/ubuntu-feisty-fawn-1/software-for-ubuntu-feisty-fawn/virtualbox-on-ubuntu-feisty-fawn"]here[/URL.

I did the fast way.

Open a terminal. In the Ubuntu desktop it's in Applications > Accessories >Terminal

Copy and paste this.

```
sudo echo
```
Make sure you type you password.

Then, copy this.

```
sudo sh -c 'echo "# VirtualBox repository for Ubuntu Feisty Fawn
deb http://www.virtualbox.org/debian feisty non-free" \
     > /etc/apt/sources.list.d/feisty-virtualbox.list'
wget http://www.virtualbox.org/debian/innotek.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get -y install virtualbox
```

Now, it looks very complicated after it's done you will find VirtualBox under the Applications menu.

Next, go to System > Administration > Users and Groups

Click on "Manage Groups".

Look for a group called "vboxusers," select it and click properties.

Under "Group Members," check all the users that you want to be able to use virtual machines and click okay.

Click "Close" and "Close" again and Start VirtualBox under Applications > System Tools > Innotec VirtualBox.

Create a new virtual machine, say whatever windows version you want, create a virtual hard disk.

You're almost done. Now select your new virtual machine and look on the right column and look for a setting that mentions CD/DVD-ROM and double-click that. Tell it to mount your host drive and click okay. Now put you windows installation disc in and fire up that Virtual Machine! Install Windows as you normally would (it varys from the different windows versions). After you install that virtual machine, you can install the programs you want (in my case, it is iTunes and Office 2003, but you may be different).

Congratulations, you successfully installed Windows in Ubuntu!:lolflag:

It worked great for me(but your results may vary.) I wish you a wonderful journey in Ubuntu!

Have a great day,

ddrplayer512

P.S. By the way, I just experienced this two to three days ago!:)

---

### Post by rsambuca on 2007-10-01
> **evolushun said:**
> LOL...ok, but remember...I am a complete moron when it comes to Ubuntu and am looking for some guidance on what to do and how to do it.  Linking me to a site is great, because in my searching, I haven't found a program that does this but linking me does not show me what to do.  I am the type of person that if you guide me on how to do something one time, I get it and understand it.  If I have to read how to do it, it goes in one eye and out the door.  I know I sound like I'm whining but this is the only problem I cannot fix and it's the only thing making me miss XP.  I just hope that someone here is drooling at the fact of getting another faithful user from Microsoft and wants to lend a helping hand.  I need to get this fixed within a few days due to certain projects needing fixed by that deadline.  Thank you again.

evolushunYou sure you don't want someone to come over and do it for you?  Or is just handholding enough?

---

### Post by ddrplayer512 on 2007-10-01
This is a seperate thing, but if you install the Virtual Box addons on the Windows Virtual Machine, you can enable a "seamless mode" and it's awesome!

Just mount the Addons Cd under one of the menus and you should start the windows installer for the addons.

---

### Post by evolushun on 2007-10-01
OK...I got it installed but got this error message when trying to run it.

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by rsambuca on 2007-10-01
It appears that you have a typo in your sources.list.  The repository that is giving you the errors should end with 'org', not 'ord'.  To correct this, you can open up the sources list file in a text editor using```
gksudo gedit /etc/apt/sources.list
```find the medibuntu repository and change the 'ord' to 'org'.  Then save the file and close gedit.

Then update your sources list by```
sudo apt-get update
```

---

### Post by evolushun on 2007-10-01
It is installing windows right now.  If I have any other questions I will post them here.  Thank you very much!

---

### Post by evolushun on 2007-10-01
Now, this is almost done installing Windows.  Will I always have to have the disk in to run Windows like this or is it a one time thing?

---

### Post by American_Outcast on 2007-10-01
I tried Virtual Box but I had some problems with it. I am now using VMwareserver and running XP on a couple of machines without any issues.

---

### Post by evolushun on 2007-10-01
OK...how do I get my external hard drive to be read on Windows AND Ubuntu?

---

### Post by ddrplayer512 on 2007-10-01
> **evolushun said:**
> Now, this is almost done installing Windows.  Will I always have to have the disk in to run Windows like this or is it a one time thing?

This is a one time thing. It is as if you are installing Windows on a real machine. Install applications and other stuff and it will stay there. A virtual machine is like having a computer within a computer.

I'll be happy to help out more if you have questions.

-ddrplayer512

---

### Post by rsambuca on 2007-10-01
What filesystem is it?

---

### Post by ddrplayer512 on 2007-10-01
Is your external hard drive USB?

---

### Post by ddrplayer512 on 2007-10-01
Wait 'till I get home, I'll try to use my iPod on my Windows Virtual Machine.

---

### Post by evolushun on 2007-10-01
My external HDD is NTFS I believe.  It connects through USB.

---

### Post by rsambuca on 2007-10-01
Then in Ubuntu just install the ntfs-3g drivers and ntfs-config to set it up for you.  In a terminal, enter```
sudo apt-get install ntfs-3g ntfs-config
```
Then you will find the NTFS configuration utility under "Applications -> System Tools".

---

### Post by evolushun on 2007-10-01
BTW...LOL...how do I shut down XP?  The same way you always do or do I just close the window?

---

### Post by themanzane on 2007-10-01
[B]I've downlaoded 7.04 yet it's an .iso file. what program do i need to make it into an install prograom, and has anyone ever installed ubuntu over windows?:lolflag:
 I'm sick of the issues with the recording software(Cubase) crashing  under windows and also can't remember the name of the program someone told me about with the name along the lines of rosebound thatruns under the ubuntu linux OS's.. If anyone could help me with the web address and any tips on openign ubuntu after downloading it i would greatly appreciate it.:guitar:[/B]

---

### Post by evolushun on 2007-10-01
I figured out how to turn it off but can someone explain to me how XP is faster and more stable as a Virtual PC than it is when it's on it's own?  LOL  This is amazing.  You have all created a lifetime Linux customer!  Thank you all for the help.  Now, if I can get my external HDD to read on both OS's, I will be as happy as a tornado in a trailer park!  LOL

---

### Post by evolushun on 2007-10-01
> **themanzane said:**
> [B]I've downlaoded 7.04 yet it's an .iso file. what program do i need to make it into an install prograom, and has anyone ever installed ubuntu over windows?:lolflag:
 I'm sick of the issues with the recording software(Cubase) crashing  under windows and also can't remember the name of the program someone told me about with the name along the lines of rosebound thatruns under the ubuntu linux OS's.. If anyone could help me with the web address and any tips on openign ubuntu after downloading it i would greatly appreciate it.:guitar:[/B]

Try this link - 

[http://www.freewarefiles.com/program_6_205_24053.html](http://www.freewarefiles.com/program_6_205_24053.html)

This will allow you to burn as an ISO file.  Other pro's here might be able to guide you in installing Ubuntu over Windows.  I had Vista and ran Ubuntu.  I then decided to install and format and I wont EVER go back to a Windows-only machine.

---

### Post by rsambuca on 2007-10-01
> **themanzane said:**
> [B]I've downlaoded 7.04 yet it's an .iso file. what program do i need to make it into an install prograom, and has anyone ever installed ubuntu over windows?:lolflag:
 I'm sick of the issues with the recording software(Cubase) crashing  under windows and also can't remember the name of the program someone told me about with the name along the lines of rosebound thatruns under the ubuntu linux OS's.. If anyone could help me with the web address and any tips on openign ubuntu after downloading it i would greatly appreciate it.:guitar:[/B]

You can find the [instructions here]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by evolushun on 2007-10-01
So, the only software I need to work in Windows requires Sound but it seems that I can't use sound because Ubuntu is using it.  Is there a workaround for this?

---

### Post by ddrplayer512 on 2007-10-01
Let me explain the benefits and disadvantages of using a virtual machine.

The benefits:

[LIST]
[*]You can run native Windows apps in Ubuntu with no problem.
[*]You are a lot safer from problems with windows because if you make a snapshot, or backup the Virtual Machine, and you have a major problem, you can just revert to the la st snapshot you made.
[*]It's just plain cool! No more dual-booting; run windows and ubuntu apps side by side.
[/LIST]

The pitfalls:

[LIST]
[*]It's a little bit slower than running Windows XP on the real hardware itself, though it is not to noticeable on faster systems and if you don't do too many applications at once.
[*]You will not get aero glass if you use Windows Vista, because it can't emulate anything but a generic video card(you probably don't care, because you have XP)
[*]But, also that lack of a better video card being emulated prevents you from playing the latest games like Bioshock and Halo 3, as they will need high-end video cards, for those you may want to dual-boot.
[/LIST]

So, that's pretty much it.

**I'll fix your sound problem.**

In VirtualBox, you will see in the right hand column a part called audio, double-click that and you will see the settings for the audio. Check the checkbox "Enable audio" and choose a host driver, but do not use the Null Audio Driver. You should hear sound. You might want to use the "ALSA" audio driver, if that doesn't work, try the other one.

---

### Post by dryder on 2007-10-01
Using this method, can you use a device (like a scanner) that does not work under Ubuntu but does under XP?

Can you leave, say, an XP native fax application running 24/7 to control all your faxing in/out while still using Ubuntu? With the fax app, that would require XP and Ubuntu to run 'simultaneously'? 


Many thanks.

David

---

### Post by evolushun on 2007-10-01
> **ddrplayer512 said:**
> 
**I'll fix your sound problem.**

In VirtualBox, you will see in the right hand column a part called audio, double-click that and you will see the settings for the audio. Check the checkbox "Enable audio" and choose a host driver, but do not use the Null Audio Driver. You should hear sound. You might want to use the "ALSA" audio driver, if that doesn't work, try the other one.

That worked perfectly.  Thank you.  I also enabled my USB ports but still can't see my external HDD.  Is this going to be possible?

---

### Post by ddrplayer512 on 2007-10-01
I appreciate the thanks. I'll try to help as best I can, apperently I am having the same problem with my iPod. Never tried to use USB before. Time for me to do some reaserch about this.
If I find an answer that works, I'll post it here.

---

### Post by evolushun on 2007-10-01
> **ddrplayer512 said:**
> I appreciate the thanks. I'll try to help as best I can, apperently I am having the same problem with my iPod. Never tried to use USB before. Time for me to do some reaserch about this.
If I find an answer that works, I'll post it here.

Thank you very much!  I know I keep saying this but I cannot believe how wonderful Ubuntu is.  It blows me away how much faster everything is and proves to me what a waste of time and energy Microsoft really is.  

One other question, not related to this problem.  Are there any good DJ programs out for Ubuntu?

---

### Post by Pumalite on 2007-10-01
[http://ubuntuforums.org/showthread.php?t=85383](http://ubuntuforums.org/showthread.php?t=85383)

---

### Post by evolushun on 2007-10-01
In regards to getting my external HDD, I have tried the following:

[LIST]
[*]In Details, I have clicked on USB and added all the peripherals that I wanted.
[*]I have also added my HDD as a shared folder but that didn't work as well.  
[/LIST]

In all, I still have yet to be able to read my HDD through XP but I am not giving up.  If anyone reads this and has an idea, please do not hesitate to offer your help.

---

