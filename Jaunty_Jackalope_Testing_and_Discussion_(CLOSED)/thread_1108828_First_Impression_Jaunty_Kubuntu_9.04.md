---
title: "First Impression Jaunty/ Kubuntu 9.04"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by CaseWestern on 2009-03-28
Awesome.  I am obsessed with it.  I have installed the beta version today on my Dell XPS M1530 Laptop 64-bit version.

Here's what I have tested:

1. Sound works fine.
2. Nvidia Latest driver 180 has been d/l from repos and graphics are working fine
3. KDE 4.2 is simply awesome - A big leap forward in the KDE dev.

4. Last but not least, Wireless worked out of box.  It worked for 8.10 too.

I have had very bad experience with 8.10 which made me switch to the rock stable 8.04 kubuntu version.  Now I am very very impressed with the beta release.  I hope the saga continues.

I added the medibuntu repos tooo.  You wouldnt' believe, but I am running it as a full fledged OS rightaway.

---

### Post by digitalmonk on 2009-03-28
How did you connect to the internet,did you use wvdial,someone posted a message saying that jaunty does not have wvdial and he was not able to connect his wireless internet.

---

### Post by CaseWestern on 2009-03-28
> **digitalmonk said:**
> How did you connect to the internet,did you use wvdial,someone posted a message saying that jaunty does not have wvdial and he was not able to connect his wireless internet.

I didnt do anything.  I think they have native broadcom drivers built in the iso image itself.  My wireless card was able to detect wireless rightaway.

---

### Post by Sonique on 2009-03-28
Cool, I am also running 64 bit Kubuntu 9.04 beta. I really like KDE 4.2, it looks really classy and seems like it has set it self up with a lot of potential to be filled in the future! Wireless has been fine (although it was in 8.04 ubuntu too). Just I found KPackageKit a bit weird so I installed Adept, I don't know the implications in that but I am just using a combination of both as well as bash.

---

### Post by ptn107 on 2009-03-28
9.04 beta x86_64 runs everything right out of the box for me with no configuration (aside installing a few codecs), period.

---

### Post by csat on 2009-03-28
I've tried out both to my desktop and notebook but couldn't complete the installation as I wish because there was no option to install boot loader onto root partition, i.e. /dev/sda12.  Installation process insists to install it to /dev/sda which would replace my Ubuntu main boot loader.

Ubuntu 8.10 gives me the choice when I click to "advanced" button right after creating user/password/computer name.

---

### Post by 3Miro on 2009-03-29
> **csat said:**
> I've tried out both to my desktop and notebook but couldn't complete the installation as I wish because there was no option to install boot loader onto root partition, i.e. /dev/sda12.  Installation process insists to install it to /dev/sda which would replace my Ubuntu main boot loader.

Ubuntu 8.10 gives me the choice when I click to "advanced" button right after creating user/password/computer name.

I guess you can not install the bootloader and then manually edit grub.

---

### Post by ahbart on 2009-03-29
I installed Ubuntu Jaunty alpha 6 on my Asus eeepc 901. Everything works out of the box. Including wifi. 
Wvdial has nothing to do with normal wireless/wifi, but it did install normally. I installed wvdial to connect with my 3G mobile broadband modem, because at first networkmanager did not pick up the modem. But after a synaptic update this week, even this Huawei modem is working via networkmanager (Vodafone UK topup and go).
I love Jaunty. Much better than Intrepid, even in alpha.

---

### Post by ahbart on 2009-03-29
> **csat said:**
> I've tried out both to my desktop and notebook but couldn't complete the installation as I wish because there was no option to install boot loader onto root partition, i.e. /dev/sda12.  Installation process insists to install it to /dev/sda which would replace my Ubuntu main boot loader.

Ubuntu 8.10 gives me the choice when I click to "advanced" button right after creating user/password/computer name.

Try the alternate download/installation. There you can specify the partition you want.

---

### Post by Sonique on 2009-03-29
> **csat said:**
> I've tried out both to my desktop and notebook but couldn't complete the installation as I wish because there was no option to install boot loader onto root partition, i.e. /dev/sda12.  Installation process insists to install it to /dev/sda which would replace my Ubuntu main boot loader.

Ubuntu 8.10 gives me the choice when I click to "advanced" button right after creating user/password/computer name.

Are you sure there is no option? I didn't need to do what you want when I installed mine, but right at the end when it says "Ready to install" - there is an "Advanced" button, and I *think* it had something there about where to put the bootloader.

Ah, look at step 7 to see the button I mean [_here_]("http://anarchismtoday.org/News/article/sid=138.html")

---

### Post by csat on 2009-03-29
> **ahbart said:**
> Try the alternate download/installation. There you can specify the partition you want.

You were right, thanks.  The Alternate version gave me the choice I was looking for.  Grub has installed indeed to (hd0,11) as I chose and I am running from this fresh new installation of Kubuntu 9.04 64 bits Beta.

Thank you all that also gave me suggestions.

:P

---

### Post by digitalmonk on 2009-03-30
hi guys,

i am using intrepid, problem is when ever firefox starts, it opens in the offline mode, also till have I have not managed to connect emapathy,it always remains offline.

does these same problem occur in jaunty beta ?

any ideas how to circumvent these??

Kind Regards

digitalmonk

---

### Post by ahbart on 2009-03-30
This has nothinh to do with Intrepid or Jaunty specifically. This is a separated problem. You should open a new thread for that. 
But, I assume you have wireless connection which is not set up directly.

---

### Post by SESF0908 on 2009-03-30
Have anyone tried to update your system after installed jaunty? I tried and it was a big mistake. When i login, it's only black screen.
I tried to fix it but..., i'm a newbie anyway :P
So i reinstall my system, and now i use ubuntu 8.04, and waiting for the final version of kubuntu 9.04.

---

### Post by Vorian Grey on 2009-03-30
> **SESF0908 said:**
> Have anyone tried to update your system after installed jaunty?
Not once but twice. All is good here.

---

### Post by digitalmonk on 2009-04-02
Hi Abhart,

You are right,I do use a wireless cdma usb modem.I use wvdial to get connected to my network.But then,I did not understand why is the proper way to set it up, so that firefox opens in the online mode and empathy gets connected.

Thanks in advance.

Anirban

---

### Post by Zorael on 2009-04-02
If we're talking impressions, I guess I'll pipe in. Kubuntu 9.04b works great for me on my slightly modified Advent 4211 netbook (rebranded MSI Wind).

It originally comes with a Sentelic touchpad of fail which doesn't work with the Synaptics driver (ergo, no drag to scroll or other nifty functionality), along with a weird Realtek wireless card that at least in 2.6.27 didn't have drivers in the kernel. So I bought a Synaptics pad and an Intel 4965AGN wireless card and replaced those two odd bits.

The only real "fixes" I always (have to) do after installing is to first tell X to use 96 dpi. For some reason, it wants to use a higher dpi font on my already small screen (~10", 1024x600). It's configurable once you've logged in (System Settings, Appearance, Fonts), but that doesn't cover the kdm greeter login screen. So I open up **/etc/kde4/kdm/kdmrc** and append **-dpi 96** to the X command arguments. Excerpt:
```
[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-br -nolisten tcp **-dpi 96**
ServerCmd=/usr/bin/X
```

Then I (really like it better if I) modify the greeter theme so that the background picture covers the whole screen. In **/usr/share/kde4/apps/kdm/themes/oxygen/oxygen.xml**:
```
        <item type="svg" id="background" background="true">
                <normal file="background.svg"/>
                <pos anchor="c" x="50%" y="50%" width="**100%**" height="100%"/>
        </item>
```
That stretches/deforms the image to fill the whole screen. Before you complain, this is how the splash screen (the one that shows what parts of the environment has been loaded before the desktop is drawn) scales, so having it otherwise would look weird. Anyway, if you want it to scale 1:1 and instead have the top and bottom cropped out, set it to **width="100%" height="scaled"**.

Hum, not sure what else. I install skim and anthy for Japanese input, and set it up to work with any and all apps. (Including GTK, Qt and XIM-only stuff, for you UIM nonbelievers out there.)
```
$ sudo aptitude install skim scim-anthy kasumi scim-bridge-client-gtk scim-bridge-client-qt scim-bridge-client-qt4 scim-gtk2-immodule

$ sudo im-switch -v -z all_ALL -s skim
$ sudo nano /etc/X11/xinit/xinput.d/skim
```
Make sure it looks as follows; the parts in bold are usually wrong/missing and makes the input support incomplete.
```
[B]XIM=SCIM
XIM_PROGRAM=/usr/bin/scim
XIM_ARGS="-d"
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=yes[/B]

if [ -e /usr/lib/gtk-2.0/*/immodules/im-scim-bridge.so ]; then
    GTK_IM_MODULE=scim-bridge
elif [ -e /usr/lib/gtk-2.0/*/immodules/im-scim.so ]; then
    GTK_IM_MODULE=scim
else
    GTK_IM_MODULE=xim
fi
if [ -e /usr/lib/qt3/plugins/inputmethods/im-scim-bridge.so ] || [ -e /usr/lib/qt4/plugins/inputmethods/im-scim-bridge.so ]; then
    QT_IM_MODULE=scim-bridge
elif [ -e /usr/lib/qt3/plugins/inputmethods/libqscim.so ]; then
    QT_IM_MODULE=scim
else
    QT_IM_MODULE=xim
fi

DEPENDS="skim, scim-bridge-client-gtk | scim-bridge-client-qt | scim-bridge-client-qt4 | scim-gtk2-immodule | scim-qtimm"
```
Then (important): start **skim** via runbox or menu entry (Utilities), right click its tray icon and hit Configure. In the *General SCIM* section, hit the *Other* tab and set *Panel Program* to **scim-panel-kde**, and *Config Module* to **kconfig**. Then in the *X Window* section, check **Start skim automatically when SCIM starts**. If that's not done, X will automatically start the (GTK) scim helper, pushing skim aside.

Then I guess I modify my **~/.fonts.conf** file to display nicer fonts, which requires **msttcorefonts**, **ttf-kochi** and **ttf-sazanami** font packages. **msttcorefonts** is nonfree software, so requires multiverse repositories.
```
$ sudo aptitude install msttcorefonts ttf-kochi-gothic ttf-kochi-mincho ttf-sazanami-gothic ttf-sazanami-mincho
```
Attaching my .fonts.conf to show an example.


Then I restart X and my system is ready for everyday use. I guess I'll want firefox and flash, but those are the foundations.

---

### Post by James Willis on 2009-04-02
It's stable and much faster than earlier versions and may be the best yet. However:

CAUTION: VERY BAD FEATURE:  The installation program automatically installs GRUB to the MBR WITHOUT ASKING PERMISSION which could mess up your system.  I was booting several versions of linux with grub menu.lst controlled by Kubuntu Intrepid which I didn't want changed.  Ubuntu 9.04 beta, although installed on a separate partition, took over with it's own menu.lst, which had left out other versions of linux and had to be manually edited to correct the problems it caused.

---

### Post by ahbart on 2009-04-02
> **James Willis said:**
> It's stable and much faster than earlier versions and may be the best yet. However:

CAUTION: VERY BAD FEATURE:  The installation program automatically installs GRUB to the MBR WITHOUT ASKING PERMISSION which could mess up your system.  I was booting several versions of linux with grub menu.lst controlled by Kubuntu Intrepid which I didn't want changed.  Ubuntu 9.04 beta, although installed on a separate partition, took over with it's own menu.lst, which had left out other versions of linux and had to be manually edited to correct the problems it caused.

Yes, I noticed that too. And that is why I prefer the alternate iso version.

---

### Post by KhaaL on 2009-04-02
The only thing I dislike about KDE4 is how unintelligent and cumbersome KRunner is compared to Gnome-do (I wonder if gnome-do works well in KDE4?).

My other gripe with KDE is that you can only scroll through tabs by scrolling the mousewhell in a limited number of apps, I'd like to see this working system-wide like in gnome.

these two things are the only things keeping me from switching over. However, I have the feeling that I'll be switching over no matter what in KDE 4.3 :)

---

### Post by SigmaSanti on 2009-04-02
I upgraded my intrepid installation to juanty and it worked okay. The nvidia driver was not the latest version, the default one is 180.3- something and the current stable one is 180.44, so I found a ppa with that version and installed it.
Other than that, everything is working well considering its a beta version and my graphics card is known to have lots of problems, its an integrated nvidia 8200.

---

### Post by Zorael on 2009-04-02
> **KhaaL said:**
> The only thing I dislike about KDE4 is how unintelligent and cumbersome KRunner is compared to Gnome-do (I wonder if gnome-do works well in KDE4?).
I don't see why it shouldn't work, though I imagine some "shortcuts" won't. Like how you can enter Fonts in krunner and have it open up the Fonts settings window otherwise accessible via System Settings -> Appearance.

Do note that krunner has plugins and settings of its own. Perhaps the gnome-do functionality you're referring to could be achieved by picking the Task oriented interface? Alt+F2, then click the wrench, User Interface tab.

---

### Post by texas.chef94 on 2009-04-10
First and foremost this is NOT an attempt to high-jack a thread but to 
1. give some impressions if someone would be so kind as to point me in the direction of a how to configure desktop. You see I received a full blown installation by fluke.
2. Was re-installing 8.10 from a stable live CD have used several times. Was installing it to a clean drive and when it finished and I rebooted I had a triple boot rather then the dual I had prior to the re-install
3. On HD I had my old 8.10 and kubuntu jaunty along with Debian 5.0 that resides on external.
Someone, anyone please advise

---

### Post by MatthewAdams on 2009-04-11
I installed a fresh copy of Ubuntu Jaunty and it is taking far too long to configure. 

Wireless didn't work out of the box, but sound did. Video settings were pretty disappointing, so I tried to reconfigure it, and crashed X. Redid my config file, fixed X, sound stopped working. Fixed sound, flash stopped working. Fixed flash. Downloaded AcidRip, took 5 hours to rip a DVD and the file was distorted. Tried K9Copy, didn't work whatsoever. Had to reboot each time I tried a new program because the DVD players wouldn't eject. Gave up and finally just wanted to PLAY the DVD at 1AM, and the DVD wouldn't play.

Theme settings kept resetting. Have to manually open my secondary hard drive before any program will detect it- tried editing the fstab file and it stopped being detected altogether. 

Came home today, tried to tune my guitar with an online tuner, and found that my sound stopped working again. 

Tried recording audio with Audacity when the sound was working, but the input, while detected, couldn't record. 



Don't get me wrong- I dig Ubuntu Jaunty, think it's going to be a very monumental release- but sometimes, I really just want to be able to come home and turn on a system that works.

---

### Post by Hydrohs on 2009-04-17
How did you get wireless working? It know what my card is and I can see all the netowrks, I can enter my WEP and everything but my internet still doesn't work, I don't see any options for it to actually connect to it or anything.

And without the internt I can't get drivers for my graphics card O_o

---

### Post by kebajonathan on 2009-04-18
yeah, how did you get wireless to work. It worked for me in 8.10 but the new applet just doesn't do anything after I enter the WPA Passphrase... Just nothing happens (I'm having the same problem on another pc with gentoo where I'm running the svn applet)

---

