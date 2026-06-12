---
title: "Flash-Drive Boot 10.04 impossible!?"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by Citta on 2013-02-15
Hi, 

I installed on a flash-drive 10.04. Restarted the netbook (Win7), the installer appeared, the count-down run down...again.....again...! Pressing "Enter" was useless! I deleted the installation from the stick, tried another version of the "Universal Installer", but no avail. Tried Kubuntu...same result. Installer menue appeared, countdown....etc.. 18 monthes ago everything worked fine, not with above mentioned installation, they were from today. I installed on a stick c't surfix, the only installation on the stick, still works. Bios boot order is ok. 
So I am a bit at loss, no clues concerning the reason for this problem.

Thanks a lot for  your hints, regards
Citta

---

### Post by oldfred on 2013-02-15
Welcome to the forums.

Do you want 10.04, it expires in April.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

For whatever reason some flash drive installer and some flash drives seem to have issues. It also may just be download or redoing it then works. 

Verify download is good.
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
    
       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Some then find unetbootin works better.
       [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
            If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Even then some flash drives seem to be an issue. I have had good luck with Microcenter house brand and Kingston with my computers.

---

### Post by Citta on 2013-02-19
> **oldfred said:**
> Welcome to the forums.

Do you want 10.04, it expires in April.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

For whatever reason some flash drive installer and some flash drives seem to have issues. It also may just be download or redoing it then works. 

Verify download is good.
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
    
       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Some then find unetbootin works better.
       [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
            If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Even then some flash drives seem to be an issue. I have had good luck with Microcenter house brand and Kingston with my computers.
Yes, I want 10.04(in a second step as dual-boot) because, as far as I remember, has 10.04 something like WindowsExplorer, which I miss in 12.04, this I have already as dual-boot. I have just once a week internetaccess, so I download everything on a thumb-drive. When plugging in this drive, I have just a bunch of icons, that is useless. I want have it with date, date added, size, type, etc. in columns and rows, for 12.04 and/or even 10.04?

Is there such a software available doing this job, or even more? How can I find such a software without loosing much time. How ist this done, what are suitable steps?
Kind regards,
Satu
PS: How can I download software and, perhaps updates under Windows on a stick and later, at home without internet installing it?
When running Ubuntu with internetaccess it takes a very long time to download or update, how can I just perform a download and installing it at home?

---

### Post by oldfred on 2013-02-19
Whether you have icons or table type view is settable in Nautilus. In view preference, default view choose list view. There are a lot of other settings for many things.

I preferred the gnome2 style with 10.10 and stayed with that until 12.04. But then I installed gnome-panel or fallback and it is very similar to the old style. On my older system with 12/04 & fallback, my system seems a bit faster than my old 10.10 install.

       Open the Ubuntu Software Centre and search for &#8216;gnome-panel&#8217;, hit install and log out.
To move/add/edit panels or applets press Alt+Right Click

            On login screen click on cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)
Restore defaults
[http://ubuntuforums.org/showpost.php?p=11968600&postcount=40](http://ubuntuforums.org/showpost.php?p=11968600&postcount=40)

 Offline Updates:
[http://keryxproject.org/](http://keryxproject.org/)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

---

### Post by Citta on 2013-02-19
> **oldfred said:**
> Whether you have icons or table type view is settable in Nautilus. In view preference, default view choose list view. There are a lot of other settings for many things.

I preferred the gnome2 style with 10.10 and stayed with that until 12.04. But then I installed gnome-panel or fallback and it is very similar to the old style. On my older system with 12/04 & fallback, my system seems a bit faster than my old 10.10 install.

       Open the Ubuntu Software Centre and search for &#8216;gnome-panel&#8217;, hit install and log out.
To move/add/edit panels or applets press Alt+Right Click

            On login screen click on cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)
Restore defaults
[http://ubuntuforums.org/showpost.php?p=11968600&postcount=40](http://ubuntuforums.org/showpost.php?p=11968600&postcount=40)

 Offline Updates:
[http://keryxproject.org/](http://keryxproject.org/)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>
Gnome I installed via terminal, done. What is this "cogwheel/star" -is it in the upper right corner? What then...or should I simply write in the browser the psychocat-address?
Thanks,
Citta

---

### Post by oldfred on 2013-02-19
If you look at the pyschocats page it shows the login screen with the logo that looks something like a star or gear in the upper right corner that you have to click on. You can choose among all the graphical DE you have installed.

---

### Post by Citta on 2013-03-25
Hi, 
I bought a Corsair, 32 GB for 36 Euro, this drive is pretty fast and everything went fine! I have several Distros as mulitboot installed. 
I did not update them-will this work?
With this "Explorer" I did not get the same view as get in Win-perhaps I should read  more or I did not understand the contents of the post?! So this problem is not solved. 
Thanks, 
Citta

---

### Post by Citta on 2013-03-25
x

---

### Post by oldfred on 2013-03-25
If you have multiple installs to flash drive it probably is just the installer version and you have to enable persistence to save anything. And I think with multiple ISO on one flash drive, you can only enable persistence for one of them.
I do have on my 16GB flash a full install of 12.04 in 8GB with 8GB of data and multiple other ISO in the data partition that I can also boot (but not save changes).

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

