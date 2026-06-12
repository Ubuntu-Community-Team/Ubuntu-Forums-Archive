---
title: "My Ubuntu went off for good after some updates"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by viriatovigo on 2014-01-29
Good morning/afternoon/evening.

After all the troubles stated in my other threats (some of them have been no been answered yet at all and other given not solution) this new "Indiana Jones trial" that seems to be a standard feature of Ubuntu.

  After clicking &#8220;Install&#8221; in some updates, now Ubuntu does not start at all. After the pink screen that says Ubuntu with 4 spots underneath going alight one after another, comes a black screen that looks like the Terminal and says:
   
  Ubuntu 12.04.4 LTS constant-X50V3 tty1
  Constant-X50V3 login:
   
  I input my username and then comes:
   
  Password:
   
  I input my password and then:
   
  Last login: Tues Jan 28 07:44:36 GMT on tty1
  Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.2.0-58-generic-pae i686)
   
     *Documentation: [https://help.ubuntu.com/]("https://helo.ubuntu.com/")
   
  constante@constante-X50V3: ''$

   
  Of course, if you go into that link what shows up is the Official Ubuntu Documentation that says nothing ab out this issue and that I already have.

And like that for the last 48 hours&#8230; What it says that I did login on Tues Jan 28 was the same.  

Now what? Take off the HDD, format it, put it back, put the Ubuntu 12.04 CD in the drive and start again? And this is the fabulous customer friendly Linux?... To do business with?

With thanks in advance for your help.

---

### Post by mörgæs on 2014-01-30
The low number of answers could be related to the tone in which you are writing.

What happens if you enter **startx** at the prompt?

---

### Post by Bucky Ball on 2014-01-30
Or in Unity (and some others) try:

sudo service lightdm start

---

### Post by mastablasta on 2014-01-30
after you try above mentioned solution - 
are you maybe using proprietary graphics drivers? did you install them manually perhaps?

---

### Post by viriatovigo on 2014-02-10
Hi everybody

Sorry, I&#8217;ve been for awhile in one of those free holidays in one of the NHS &#8220;holiday spots&#8221; that I use to visit time to time after the stroke.

I am writing from the MacBook Pro because I can&#8217;t use the PC with Ubuntu, obviously, since I am getting a black screen with the terminal prompts.

**mörgæs**: After entering startx I get a black screen and gets frozen. I need to switch it off and on again to get again the same prompts.

**Bucky Ball**: After switching on again the PC, imputing my username and password and entering sudo service lightdm start, comes a serie of lines that say:

starting mDMS/DMS-SD deamon                                                                                                 [ OK ]
starting Bridge socket devents into upstart                                                                                   [ OK ]
Stopping cold plug devices                                                                                                          [ OK ]
Stopping log initial device creation                                                                                               [ OK ]
Starting configure network device security                                                                                    [ OK ]
Starting configure virtual network devices                                                                                     [ OK ]
Starting save udev log and update rules                                                                                        [ OK ]
Stopping configure virtual network devices                                                                                    [ OK ]
Starting network connection manager                                                                                           [ OK ] 
Stopping Userspace bootsplash                                                                                                    [ OK ]
Stopping save udev log and update rules                                                                                      [ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Starting AppArmor profiles                                                                                                           [ OK ]
speech-dispatcher disable: edit /etc/default/speech-dispatcher
Stopping System V initialisation compatibility                                                                                 [ OK ]
samed disable: edit /etc/default/saned
Starting System V runlevel compatibility                                                                                        [ OK ]
Starting crash report submision daemon                                                                                        [ OK ]
Starting automatic crash report generation                                                                                    [ OK ]
Starting regular background program processing daemon                                                               [ OK ]
Starting LightDM Display Manager                                                                                                 [ OK ]
Starting ACPI daemon                                                                                                                  [ OK ]
Starting anac(h)ronistic cron                                                                                                         [ OK ]
Starting save kernel messages                                                                                                      [ OK ]
Starting deferred execution scheduler                                                                                            [ OK ]
Stopping Send an event to indicate plymouth is up                                                                         [ OK ]
Stopping anac(h)ronistic cron                                                                                                        [ OK ]
Stopping save kernel messages                                                                                                     [ OK ]
Starting CPU interrupts balancingdaemon                                                                                       [ OK ]

(flashing the hyphen without stop and doing nothing else)    


**mastablasta**: I don&#8217;t know and I have not a clue what that means.

---

### Post by mörgæs on 2014-02-11
You have had a lot of trouble with 12.04, it seems. 
How does it work in a fresh install of 13.10?

---

### Post by mastablasta on 2014-02-11
> **viriatovigo said:**
> **mastablasta**: I don’t know and I have not a clue what that means.


it means: are you using closed source graphic chip drivers such as those made by AMD or Nvidia?

---

### Post by viriatovigo on 2014-02-11
Thank you both for helping me... I mean at least you try... The problem is the "animal" in two legs in this side of the pond that is too thick.

mörgæs: Good point... Were none before the bl**dy update... Never ever again I will click in "Update" in Linux. "How does it work in a fresh install of 13.10?" - You tell me how because I can't open Ubuntu as I keep saying.

        mastablasta: I don 't know and now I have not way to know it because I can't open Ubuntu as I keep saying and look into my computer. In any case I can't remember if I did update drivers myself because I did set Ubuntu to do it automatically in the beginning, one year ago. I can't remember how, I think that I did it by following someone's else advise.

---

### Post by viriatovigo on 2014-02-11
mörgæs... I remember now that I did try to upgrade 12.04 to 13.10 in the past and was a total mess and I had to reinstall 12.04 because it was a huge mess, nothing did work at all, so following the advise in the Forum I did manage to install 12.04 afresh.

By the way, when I do switch on the PC, input my username and password, in the terminal that shows up, it shows that there are "22 packages can be updated" and "9 updates are security updates"... Certainly, when I could manage to open Ubuntu, no way that I am going to install them and go back to the same nightmare again.

And I am not alone... I've found more than 400 people in 4 forums with the same problems -past and present- than me and much more, and no one did manage to resolve them. At least the 80% of them did try to uninstall Ubuntu and no one could do it (including me, that I had to format the HDD to get rid of it). It seems that, once in, there is no way to get rid of it (it preforms like a virus...).

---

### Post by mörgæs on 2014-02-11
You can uninstall a Buntu system in a live boot using Gparted. 

The number of people posting a problem says nothing about the magnitude of the problem. We never hear from installations where everything works so there's no way to compare.

Your hardware has an Atom processor, which receives better support in 13.10. If you don't have anything of value on the system I suggest that you simply install 13.10, erasing the old version in the process.

---

### Post by viriatovigo on 2014-02-11
Ta mörgæs.

I've got the message... Thank you for the teaching.

Nop! I have nothing of value or no value at all since I didn't manage to make it work properly. Now... How to install anything if I can't open the system? I suppose that it is going to be through the terminal, which is the solo thing that opens in full screen. 

To make it clear, I'm going to write what comes on when switching on the PC:

Ubuntu 12.04.4 LTS constante-X50V3 tty1

constante-X50V3 login:
Password:
Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.2.0-58-generic-pae i686)

* Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)

22 packages can be updated.
9 updates are security updates.

constante@constante-X50V3:&#713;$


What next?

---

### Post by Bucky Ball on 2014-02-11
Well, the obvious thing would be to:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... and see if it gets you any further or even fixes, but as this experience has given you somewhat of an unhealthy phobia about updating, you probably won't do this. A crash can sometimes occur when a machine is eventually updated after not being updated for ages.

'Never updating again' is extremely unwise and will leave your machine vulnerable as you will not be receiving security updates. If you intend never to update again, I advise you take this machine offline.

---

### Post by mörgæs on 2014-02-12
You just create a bootable USB stick with 13.10 and install from that, forgetting everything you have on the hard disk.

After that it's advisable to upDATE (within the version number) but not upGRADE (to the next version). Fresh install of 14.04 when that time comes.

---

### Post by viriatovigo on 2014-02-13
Hi Bucky Ball and mörgæs.

Bucky Ball: Oh! Forget my old man Mediterranean bad temperament. What needs to be done must be done. I am not going to waste the time of the people in this forum for nothing. I did run your scripts and, as I suppose that you did expect, a lot of lines come on ant the last two after the last script are "Calculating upgrade... Done", "0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade", and then the typical "constante@constante-X50V3~$" and flashing hyphen. Now what?

mörgæs: I suppose that you mean to download 13.10 in one of the other PCs because in this one I can't do nothing or I don't know how to do it. Is it? By the way, I saw your profile and where you are. Interesting... I used to be around with my sailing boat before the stroke. How can I make any particular comment out of the thread?

---

### Post by Bucky Ball on 2014-02-13
> **viriatovigo said:**
> How can I make any particular comment out of the thread?

Depends if it's a passing comment or a conversation. The latter would be via PMs, if the other party is willing. We generally avoid letting threads get (too) off-topic, for obvious reasons. ;)

---

### Post by viriatovigo on 2014-02-13
Thanks Bucky Ball.

I did understand that, that's why I did ask to mörgæs how to do it. It is up to him if he is willing to start a chat or he doesn't. In any case it means nothing, was just to make some comments with not relevance about something that has not relation with the thread, this forum, Ubuntu or Linux at all.

Right... After what I told you last time I did restart the Shuttle but nothing new. Again the black terminal in full screen with the usual lines, but now it doesn't show any updates what means that updates have been installed. What says is:

Ubuntu 12.04.4 LTS constante-X50V3 tty1

constante-X50V3 login: xxxxxxxxx
Password:
Last login: Thu Feb 13 18:40:02 GMT 2014 on tty1
Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.2.0-58-generic-pae i686)

* Documentation: [http://help.ubuntu.com/]("http://help.ubuntu.con/")

constate@constante-X50V3:~$  (and the flashing hyphen)


As you can see does not show the standing updates, so I infer that have been installed.

What next?

---

### Post by viriatovigo on 2014-02-13
mörgæs:

If I use other PC I need to install the [Pen Drive Linux's USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") as per [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Now... If I do that, What next? Should I plug the memory stick into the Shuttle and restart the PC?

Also I am not sure if Windows or Apple is going to let me to install something from Linux... I don't know... What do you think?


Sorry... I am not confident with this process... I did try to install it but I do understand that tells me to install it in the Ubuntu Desktop, but... If I can't open  Ubuntu!!!!!

Nop! It says that to create the  bootable flash drive I need to do it with Windows XP, 7, Vista or WINE and I have none of those. Also my stick is exFAT, no FAT16, FAT32 or NTFS as required.

---

### Post by mörgæs on 2014-02-14
The two links above are fine.
 
Basically you just install 13.10 the same way you tried to install 12.04: Create a USB stick and boot with it attached. You can create the USB in any Windows or Buntu version.

I'm not much online the next couple of days but you can always try to send a private message.

---

### Post by viriatovigo on 2014-02-14
Thank you mörgæs,

I couldn't make work the CD downloaded from the net either (but did work the previous time...) so in the end I did buy a CD from Canonical and it worked, but I will have a go with the stick and see what happens.

Thank you for allow me to send you a private message. I suppose that can be done using the link in the menu in the top of this page "Private Messages", Isn't it?

By the way... I could install the 12.04 and install the 13.10 straightaway but "You can uninstall a Buntu system in a live boot using Gparted" = Ho to do that if the OS doesn't start? Through some scripts in the terminal? Which scripts? And, what is Gparted?

---

### Post by Bucky Ball on 2014-02-14
Click on the user's name to the left (or above) their post. A menu will pop up. Choose 'Private message'. ;)

---

### Post by viriatovigo on 2014-02-15
Good morning Bucky Ball

And thank you for the tip. It is a lot quicker... Unfortunately I did send already a message  by the long way: Clicking in the top of the page on "Private Messages" and filling the form.

Just learning...

Have a nice day (out of the snow...). Over here we are using boats instead cars...

---

### Post by mörgæs on 2014-02-15
Thanks for the message.

You don't have to uninstall the old system. It will be erased automatically during setup.

---

### Post by viriatovigo on 2014-02-16
Good evening/morning mörgæs.

I've just downloaded the installer and the 13.10 in the memory stick.

Now... Do I plug the stick into the PC USB socket and restart the PC? Is this correct?

---

### Post by viriatovigo on 2014-02-16
Right... I did it. I mean restart the PC withe USB stick plugged. 

At PC start up I did chose to boot from the USB stick and now a Ubuntu window titled "GNU GRUB   version 1.99-21ubuntu3.14" asks me to chose one of the following options:

Ubuntu, with Linux 3.2.0-58-generic-pae
Ubuntu, with Linux 3.2.0-58-generic-pae (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

In the bottom says "Use &#8593; or &#8595; keys to select which entry is highlighted. Press enter to boot the selected OS, 'e' to edit the commands before booting or 'c' for a command-line."

What to do next?

---

### Post by Bucky Ball on 2014-02-16
Choose 'Ubuntu, with Linux 3.2.0-58-generic-pae' and login? Looks like you are there and ready to roll.

---

### Post by mörgæs on 2014-02-17
A kernel of 3.2.x indicates that you are booting from the hard disk (12.04) and not the USB stick (13.10). 
You need to change boot order in BIOS.

---

### Post by viriatovigo on 2014-02-17
Good morning Bucky Ball and mörgæs:

Bucky Ball: Nop! Doesn't work. It comes back to:

Ubuntu 12.04.4 LTS constante-X50V3 tty1

constante-X50V3 login: xxxxxxxxx
Password:
Last login: Thu Feb 13 18:40:02 GMT 2014 on tty1
Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.2.0-58-generic-pae i686)

* Documentation: [http://help.ubuntu.com/]("http://help.ubuntu.con/")

constate@constante-X50V3:~$  (and the flashing hyphen)

mörgæs: Well... I have set

1st Boot Devide                        (USB Hard Disk: Kingston 101 G2 PMAP)       (That is the memory stick)
2nd Boot Device                       (USB CD/DVD: TSSTTcorpCDDVDM S...)        (That is the CD drive with the Ubuntu 12.04 disc inside)

And didn't work. It comes a lot of can not reset ports and errors and in  the end "failed" and the flashing hyphen without stop but does nothing else.

If I chose the 2nd Boot Device the PC Hard Drive it comes the same than in the case of Bucky Ball.

The other options to boot are:

USB Key
UEFI: KingstonDT 101 G2 PMAP
Network
USB Floppy
CD/DVD

What I am doing wrong this time?

---

### Post by mörgæs on 2014-02-18
You are now back to installing 12.04, why?
How did you install the present (semi-working) system, from DVD or USB?

---

### Post by viriatovigo on 2014-02-18
Hi mörgæs.

&#8220;You are now back to installing 12.04, why?&#8221; - No, I am not...

&#8220;1st Boot Devide (USB Hard Disk: Kingston 101 G2 PMAP) (That is the memory stick)
If I chose the 2nd Boot Device the PC Hard Drive it comes the same than in the case of Bucky Ball.&#8221;

So, what happens when I boot from the stick memory and choosing as 2nd Boot Device the PC Hard Drive what comes up is a black terminal full screen with:

&#8220;Ubuntu 12.04.4 LTS constante-X50V3 tty1

constante-X50V3 login: (my username)
Password: (my password)
Last login: Thu Feb 13 18:40:02 GMT 2014 on tty1
Welcome to Ubuntu 12.04.4 LTS (GNU/Linux 3.2.0-58-generic-pae i686)

* Documentation: [http://help.ubuntu.com/](http://help.ubuntu.com/)

0 packages can be updated
0 updates are security updates.

constate@constante-X50V3:~$ (and the flashing hyphen)&#8221;

But it doesn&#8217;t reboot at all from the USB memory stick with the 13.10 on it.

&#8220;How did you install the present (semi-working) system, from DVD or USB?&#8221; - As I said 4 days ago &#8220;I did buy a CD from Canonical and it worked&#8221;, because I couldn&#8217;t install it from the CD downloaded from the net either. The "semi-working" system was fully working before the updates, so the Canonical CD is good.

Just now I did try again to boot from the memory stick with the same result stated above.

Again, the boot options are:

USB Hard Disc : KingstonDT 101 G2 PMAP (that is the plugged memory stick with 13.10)
Hard Disc : WDC WD3200LPVX-0... (that is the PC HDD)
USB CD/DVD : TSSTcorpCDDVDN S... (that is the empty CD drive)
USB key
UEF I : kingstonDT 101 G2 PMAP 
Network
USB Floppy
CD/DVD

And the priority is in this same order, so the 1st Boot Device is the memory stick and the 2nd Boot Device is the PC HDD.

Should I buy again another CD from Canonical with Ubuntu 13.10 on it? Because it is obvious that anything downloaded from the net doesn&#8217;t work at all, whatever be on a CD or on a memory stick (I mean I don't know how to do it properly).

---

### Post by viriatovigo on 2014-02-18
Before you ask me what is in the memory stick...

After following the links that you advise me that they were ok (Pen Drive Linux's USB Installer as per [http://www.ubuntu.com/download/deskt...ick-on-windows](http://www.ubuntu.com/download/deskt...ick-on-windows)), I did put in the memory stick the Pen Drive Linux’s USB Installer and the Ubuntu 13.10.

So, now, in the memory stick plugged in a Suttle’s USB sock are:

ubuntu-13.10-desktop-amd64.iso
Universal-USB-Installer-1.9.5.2.exe

---

### Post by mörgæs on 2014-02-18
> **viriatovigo said:**
> 
ubuntu-13.10-desktop-amd64.iso
Universal-USB-Installer-1.9.5.2.exe

None of these files should be on the USB stick. 

First, the .exe file must be installed in a Windows system. Please post back when that is working.

---

### Post by viriatovigo on 2014-02-18
I've found this link but now I understand less... [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

It says that can not be used a USB stick but a flash drive (?????????????????). I thought that was the same thing but called differently... My stick is more than enough, is 64GB. I did the stick using a Mac OSX (this MacBook Pro with Maverick).

What is a USB-creator? What has to do a CD drive in this business? 

It says "If you want to boot in UEFI mode and install your Ubuntu flavour alongside Windows, you should use for example the **ubuntu-13.04-desktop-amd64.iso** directly". precisely what I have in my stick but I am not trying to put it in the Lenovo with Windows 8 (Should I?) but ion the Shuttle that has not previous OS, the first one was 12.04 until the bl**dy updates.

I found the information totally confusing and means nothing to me... I am not at that level I am afraid (I am not at any level... I am thick like a brick).

---

### Post by Bucky Ball on 2014-02-18
13.04 has reached end-of-life and is no longer supported. Time for plan B.

Flash drive, USB stick/dongle, thumb drive = the same thing.

---

### Post by viriatovigo on 2014-02-18
Sorry mörgæs.

My last post did cross with your last post, so when I was writing it and sending it still I had not yours, it did show up immediately after I did send mine.

What do you mean? That I must download both files in the Lenovo with Windows 8?

---

### Post by Bucky Ball on 2014-02-18
You install this in Windows: Universal-USB-Installer-1.9.5.2.exe

You then launch it and when it asks for the image you want to burn to USB, you point it to this: ubuntu-13.10-desktop-amd64.iso

You then reboot and set the machine to boot from the USB stick.

---

### Post by viriatovigo on 2014-02-18
Hi Bucky Ball.

Sooorry? Do you mean that 13.10 is not supported but 12.04 is supported? But if 13.10 is newest than 12.04... I don't get it...

"Flash drive, USB stick/dongle, thumb drive = the same thing" - "That" is what I thought but the Ubuntu help doesn't opines the same... it seems to me... I use myself more "dongle" than anything else.

As I said to mörgæs, I am not installing it in a Windows machine at all but in a Shuttle without OS. The first OS that I put inside was 12.04. The Shuttles X50V2 and V3 come without OS, RAM, HDD, keyboard, mouse and without CD drive, are designed to each one finish it as he/she pleases. I've got one for someone else and finish it with a Windows 7 inside and this one for me with Ubuntu 12.04.

---

### Post by Bucky Ball on 2014-02-18
You said:

> ... you should use for example the ubuntu-13.04-desktop-amd64.iso directly". precisely what I have in my stick ...

I realise now that you actually mean you have 13.10 on your stick, not 13.04, so disregard. ;)

---

### Post by viriatovigo on 2014-02-18
Right mörgæs.

I have now in my Lenovo, in Windows 8, on "Downloads":

ubuntu-13.10-desktop-amd64               Type: Disc Image File
Universal-USB-Installer-1.9.5.2             Type: Application

Fanny thing (to me of course): When I open properties of Universal-USB-Installer-1.9.5.2 it says "Description: Universal Linux UFD Creator", and in "Open" says "Program Name: Universal-USB-Installer-1.9.5.2.exe". So, was "that" what that link meant with "USB-creator"? Still I found that information confusing.

Also opening the properties of ubuntu-13.10-Desktop-amd64 says "Name: ubuntu-13.10-desktop-amd64.iso".

What next?

---

### Post by Bucky Ball on 2014-02-18
See post 35.

---

### Post by Iowan on 2014-02-18
> **viriatovigo said:**
> 
Sooorry? Do you mean that 13.10 is not supported but 12.04 is supported? But if 13.10 is newest than 12.04... I don't get it...
12.04 is LTS (Long Term Support)... 13.10 is not

---

### Post by viriatovigo on 2014-02-18
Hi Bucky Ball.

Hold on, hold on...

"You then launch it and when it asks for the image you want to burn to USB, you point it to this: ubuntu-13.10-desktop-amd64.iso

You then reboot and set the machine to boot from the USB stick"

The ubuntu-13.10-desktop-amd64.iso is also in the Windows Downloads... The Universal USB installer is also in Windows Downloads... What has to do here any USB and any stick? Were is the stick? 

Somewhere between "You then launch it and when it asks for the image you want to burn to USB, you point it to this: ubuntu-13.10-desktop-amd64.iso" and "You then reboot and set the machine to boot from the USB stick" something is missing... Where is the link between the first sentence and the second sentence? Was supposed to have the stick plugged? What for if so far was nothing done on it? Sorry body, but I am too thick... I do apologize...

---

### Post by Bucky Ball on 2014-02-18
Ok. You want to create a bootable Ubuntu USB so you can install Ubuntu? If you do, plug in the USB stick and 

1/ Double click the Universal USB installer .exe and install the program onto your COMPUTER;
2/ Launch the Universal USB installer program from your applications menu;
3/ Choose the ubuntu-13.10-desktop-amd64.iso as the image you want to use to create the bootable USB stick;
4/ When all that is finished and the USB creation process is complete, reboot your machine;
5/ Enter the BIOS on reboot or hit whatever key you need to to select the boot device and choose the USB.

That's it. You should now be installing Ubuntu 13.10 from the USB stick.

---

### Post by viriatovigo on 2014-02-18
Ta Bucky Ball.

"You want to create a bootable Ubuntu USB so you can install Ubuntu?" - Of course! That is the issue since the post 13 by mörgæs...

OK, I am going to perform your steps and I'll be back to you with the results.

Sorry Iowan, very sorry, but I missed your post for some reason. I've found it now looking for the post in which mörgæs did advice me to boot from a dongle. So Linux starts behaving like Microsoft, each new version last less and the support gets stopped before the new version starts to get hold... Very interesting... So, where is the point?

---

### Post by Bucky Ball on 2014-02-18
This is getting awfully confusing. LTS releases are now supported for five years, used to be three, so that is two years longer. The interim releases (anything not an LTS) are now supported for nine months, used to be eighteen, so that is shorter. 

The point is if you want a long support release use an LTS. If you want to try newer software and don't mind regular OS upgrades, use the interim releases. Interim releases are upgradeable to the next release (13.04>13.10 for instance), but ONLY that. LTS releases can upgrade to the next release (12.04 LTS>12.10 for example) OR LTS to LTS. So, 12.04 LTS is directly upgradeable to 14.04 LTS when it comes out in April, leapfrogging all the interims in between.

To upgrade from 12.10 to 14.04 would mean 12.10>13.04>13.10>14.04 LTS. A long and problematic route to which the only advice would be to do a clean install.

---

### Post by viriatovigo on 2014-02-18
Ta Bucky Ball.

I this moment is being installed in the stick.

I see... It is the same than Apple. To get the Maverick that I have now, I had to start with Leopard, then upgrade to Snow Leopard, then upgrade to Mountain Lion and finally to Maverick.

But I can see that in case of Linux can not be done because the step 13.04 is not supported anymore, so I suppose that the best bet is format the HDD and install afresh. Not very helpful... Linux is not customer friendly at all and now this. Hold on, the installation in the dongle has finished. I going to reboot the Shuttle with the dongle and fingers crossed.

Talk to you later.

---

### Post by Bucky Ball on 2014-02-18
> **viriatovigo said:**
>  Linux is not customer friendly at all ...

You haven't had the best experience. Many others have had very few or no problems installing. I install Ubuntu, on average, about once a month and rarely have any issues, but then I have been using it for awhile and done it before.

It can depend on all sorts of things; hardware configuration, user experience level, Linux distribution, time of day, position of the moon, alignment of the planets, whether you do a little dance, sing a little tune and throw some salt over your shoulder while it is installing (well, maybe not the last few things). ;)

UEFI has been a bit of a stumbling block, but Ubuntu is getting past that issue now.

---

### Post by viriatovigo on 2014-02-18
Bucky Ball!!!!

YES!!! BINGO!!!

Is 3 am over here but I am going to open a case of Guinness... Oh yes! 

You make my week... 

Thank you very much.

All the best. Have a beautiful day.

Tino

---

### Post by Bucky Ball on 2014-02-18
Rock on! Have one for me and the other helpers. ;)

Please mark the thread as solved to help others by following the instructions in my signature link. Cheers and enjoy!

PS: Post new threads for any further issues or questions in the appropriate forum sections.

---

### Post by mastablasta on 2014-02-19
> **viriatovigo said:**
> But I can see that in case of Linux can not be done because the step 13.04 is not supported anymore, so I suppose that the best bet is format the HDD and install afresh. .


just in case somoene else stumbles upon this thread - it is possibel to upgrade EOL releases: [URL="https://help.ubuntu.com/community/EOLUpgrades"]https://help.ubuntu.com/community/EOLUpgrades
[/URL]
however it might be easier and cleaner to just backup important data (which should be done before upgrading as well) and perform a fresh install.

---

### Post by viriatovigo on 2014-02-19
Hi everybody.

Sorry for being so rude and not to thank to everyone that did his best to help me.

After &#8220;recovering&#8221; for a feast of Guinness in a party of two with the chap in the mirror at 4 am, I wish to thank for their help to Iowan, mastablasta, Bucky Ball and mörgæs for their patience with my bad Mediterranean temper, my lack of knowledge and skills and all their struggle to make me to understand what even a brain dead could understands but me.

In this sense, mörgæs have been far beyond of what can be called &#8220;normal human patience&#8221; and he kept helping me until the end. He has been very polite and educated and made me to realize that is not point behaving like a spoiled child and be a &#8220;normal&#8221; human being. His &#8220;The low number of answers could be related to the tone in which you are writing.&#8221; was the best lesson I&#8217;ve got for a long time. As I said, because he is very polite but if the &#8220;compliment&#8221; had came from the Mediterranean side I should had to hear a lot of greetings to my mother...  and in the end, of course, I would not have resolved the issue because everybody would have gone to see TV and mentally had said &#8220;drop dead, you d*mn bl**dy idiot!&#8221;.

Bucky Ball didn&#8217;t make any &#8220;comment&#8221; but repeated the instructions again and again like written for a person with Down Syndrome otherwise I wouldn&#8217;t understand a dot. 

All the best to every one.

---

### Post by mörgæs on 2014-02-19
Thanks for the kind words and good luck with Buntu.

---

