---
title: "Difficulty with installing Ubuntu 12.04 LTS"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by Emcee2ice on 2012-12-22
Hi All,

I'm writing to request your assistance, having tried and failed severally to install Ubuntu 12.04 LTS on my Sony Vaio (VGN-BZ1).  My intention is to have Ubuntu cohabit my machine alongside Windows. 

The main issue has been with getting my machine to boot to the bootable USB flash disk that I generated using Linux Live USB creator.  I did change my boot device order using BIOS setup functions.

Many thanks for your urgent assistance.

Emcee2ice

---

### Post by stunningman on 2012-12-22
first install windows than linux
1.if windows already installed and you want to make your system to dual boot make use of your other partition.
2.now put your ubuntu cd or dvd or usb drive and boot system and make sure that the first boot option in your bios is set to cd, dvd or usb so that when you restart your system it reads from there.
3.wait for some minutes it can be long depending upon your ram to show the main screen
4.when you reach the main screen there is an install option available there it will ask for your basic details and then it will ask for the partition in which you want to install ubuntu
in this screen choose to install ubuntu manually
5.choose the partition other than the partition in which your windows is installed otherwise it will erase your windows partition
6 after selecting the desired partition there is a small check box beside it tick it.and choose it as root look like this "/"
7.make a swap partition say you have 2gb ram than make this partition 4gb in your harddisk

and voila its done
enjoy Ubuntu\\:D/

---

### Post by Emcee2ice on 2012-12-22
stunningman, thanks for response. But, your reply misses the critical issue  that I need help with: My machine is not booting to the bootable USB flash disk that I generated.

My understanding is that your instructions would only apply if I could boot to the Ubuntu USB.

Thanks.

---

### Post by audiomick on 2012-12-22
Firstly, that is an older machine, isn't it? If I'm not mistaken, that is a model that I was rather interested in some time back. If it is an older machine, that might be relevant to it's ability to run the latest Ubuntu.

It would help if you could give some details. "It wont boot" doesn't say much. Does the machine simply completely fail to see the USB stick? Does it start to boot and then fail? Does it get nearly all the way and then have trouble displaying the screen?

If that is really the machine I think it is, it might just be old enough to have trouble booting from USB...

---

### Post by Bucky Ball on 2012-12-22
*Thread moved to** Installation & Upgrades***

---

### Post by UltimateCat on 2012-12-22
Hi Emcee2ice:

I have a Sony Vaio too.

Recently I installed Fedora on it with out any problems.

It's a new Vaio but I'm thinking that it shouldn't matter- (if so I stand corrected)

Anyway after I burned Linux on a DVD/CD I was on the Windows side and opened the CD Drive and placed the Live Cd in hurried up and shut down the Vaio.  I then waited about 30 seconds and turned the Vaio on and it immediately started to read the DVD/CD and I started the install.

Did you already reach the partitioning scheme and tell the partitioning manager to write the changes to disk?
If so and you partitioned it wrong your Vaio won't boot up.
If this is your case; you will have to re-partition again. (start the install all over again)

If your Vaio won't boot at all try holding down the power button for a longer period and see if that works.

Did you shrink the Win's operating system (NTFS) before you started your Linux install?  What version of Win's is it; XP? Vista? or Win's 7?

You said:
>   I did change my boot device order using BIOS setup functions.

In what order did you change your device boot order; to boot the usb drive first?
If that's not working you might only be able to boot to the CD Rom drive only.

Do you suspect hardware failure?

Sorry so many questions; but I'm trying to help-

---

### Post by UltimateCat on 2012-12-22
Sony's Customer Service phone #

1-877-865-7669

Sony sent me the Win's Recovery disc's but I also made 5 Recovery disc's just in case.  Did you make the Recovery Media when you had your Vaio firsthand?

---

### Post by Emcee2ice on 2012-12-23
Hi audiomick,
I'm sorry, I don't know what you mean by "older machine". I bought
 my Vaio in September 2009. Does that make it an "older machine"?!
 However, there's no indication anywhere in the Ubuntu
 documentation that machines bought during and/or before this time
 may not be able to run Ubuntu 12.04 LTS. Please, can you provide
 more details on your reasons for thinking that this machine may not
 be able to run Ubuntu 12.04 LTS.

The machine does not see the USB stick when booting, so boots to
 Windows. Is there any way around this?

Thank you, audiomick.

Emcee2ice

---

### Post by Open and Sourced on 2012-12-23
You probably should reinstall the whole system.

---

### Post by oldfred on 2012-12-23
About half way down in this Microsoft page is a list of the keys used to get into BIOS or one time boot keys for most major vendors.

       Boot keys
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

    
Both change BIOS and try one time boot key if necessary. If it still does not work then it may be an issue with brand of  flash drive, some for whatever reason do not work. Or how flash drive was written.

Other installers sometimes work.
       [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by Emcee2ice on 2012-12-23
Thanks a lot, UltimateCat, especially for the many questions you've asked me! I know that you are really out to help me.

Believe it or not, your questions have inspired me to think deeply about the Ubuntu installation steps that I've executed. I need to backup all my files and programs, recreate my VAIO system restore DVD to ensure it's fully operational, re-partition my hard-disk drive, and then try re-installing Ubuntu 12.04 LTS. Unfortunately, I haven't the dual layer DVD+/-R required for some of these tasks at the moment. BUT, I'll let you know what happens once these tasks are completed. 

Thank you once again, UltimateCat.

Emcee2ice

---

### Post by audiomick on 2012-12-24
> **Emcee2ice said:**
> Hi audiomick,
I'm sorry, I don't know what you mean by "older machine". I bought
 my Vaio in September 2009. 


Then it is not the one I was thinking of. The one I had in mind was a about 6 or 7 years ago. A machine from 2009 should easily deal with 12.04.

---

