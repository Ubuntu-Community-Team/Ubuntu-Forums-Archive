---
title: "Lubuntu desktop to cinnemon desktop to dead desktop (without asking)"
date: 2017-12-10
forum: Installation &amp; Upgrades
---

### Post by shabidoo on 2017-12-10
Twice I have installed lubuntu on my low-spec laptop (love it by the way). After a few uses, it loads automatically into cinnamon. On cinnamon it significantly slows down, I don't particularly care for it and worst and I cannot play any videos anymore. The first time I tried to remove cinnamon and when it booted up again, it gave me a dead desktop. After reinstalling lubuntu, after half a week, it loaded into cinnamon again. This time I logged off and it gave me a couple strange options: cinnamon, cinnamon safe or lxqt. Since lxqt was the only non-cinnamon environment so I logged into it. This also led me to a dead desk-top. By dead desktop I mean:I can only click on the icons, they open up programs but I can only open up programs with an icon. There is no doc or menu bar. The first time I logged in there was wall paper  with a bird. I restarted the computer and then had a black background with the icons missing (only the labels) with tiny trace outlines, otherwise black. Since I cannot open the terminal I cannot try any fixes. Shortcuts don't work. I tried logging into the various versions of lubuntu (three versions and their safe modes). I have two linuxes on other partitions (LXLE and MXLinux) and they load totally fine. But I want lubuntu because its much faster and offers exactly what I need. I've never had anything like this happen on this laptop (windows or linux). Disclaimer: I'm not super linux literate. Is there anything I can do to get my old screen back? If not, and I reinstall lubuntu...is there something I can do to avoid this happening again?

---

### Post by RobGoss on 2017-12-10
If you've installed another desktop on top of Lubuntu, it might be worth doing a fresh installation of Lubuntu because there will be unwanted software on the system

---

### Post by shabidoo on 2017-12-10
> **RobGoss said:**
> If you've installed another desktop on top of Lubuntu, it might be worth doing a fresh installation of Lubuntu because there will be unwanted software on the systemHi Rob. Thanks for replying. I installed LXLE and MXLinux on different partitions and created a new partition for Lubuntu. Is it possible that conflicts can happen between different distributions on different partitions? I'd prefer to not wipe the whole harddrive and only install lubuntu but would if you think it's a probable solution.

---

### Post by DuckHook on 2017-12-10
If you loaded Lubuntu onto an existing partition that used to hold Cinnamon without forcing the reformatting of that partition as part of your install process, then it may be possible to inherit the old Cinnamon files. I've never tried this, so it's just a rather wild guess.

Otherwise, I can't see how Cinnamon would have been installed into your Lubuntu partition, unless you installed Cinnamon at some point by mistake. Lubuntu simply does not come with Cinnamon by default. It has to be either added, or inherited.

It is like pulling teeth to get rid of a DE once it has been installed. There are too many packages that make up a DE and purging the metapackage does not, in fact, get rid of the real packages that collectively make up the DE.

You don't need to wipe your whole HDD. The other two distros can remain. Installing a fresh instance of Lubuntu should be enough *provided it is truly isolated to its own partition*. This last point is worth checking: you may have inadvertently installed Lubuntu onto a partition that you weren't counting on. Have a look through your partitions with the partition viewer of your choice (like *gparted*). If you think it would help, you can post back the output of the following:```
sudo parted -l
``````
sudo fdisk -l
```The point of the above would just be to double check your actual partition layout. If posting, please add explanations for which partitions are being used for what purposes. And please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by shabidoo on 2017-12-10
Hi Duck Hook. I created a new partition just for Ubuntu. I ran the two commands you gave me.  Gparted wouldn't open...perhaps because one of the partitions is mounted? I cannot get the text to have hard breaks so I'm uploading a screencapture of the two commands you gave me.I looked up about the warning about cylindars. Im not sure i entirely understand it but it seems like that might explain the problem?

---

### Post by deadflowr on 2017-12-10
> Is it possible that conflicts can happen between different distributions on different partitions?
No. Not unless you set a home partition that they all share. ( Or if you tried to get funky and let them all share a system directory or two like the /lib directory, which would be total non-sense if you tried to do that)

Two general questions:

How'd you install cinnamon?

And what version of Ubuntu? (version being 14.04 or 16.04 or 17.10)

It may be as simple as reinstalling the lubuntu-desktop package.

---

### Post by DuckHook on 2017-12-11
> **shabidoo said:**
> Gparted wouldn't open...perhaps because one of the partitions is mounted?
My bad. Command should be:```
sudo parted -l
```
I've also corrected my original post so as not to confuse lurkers.

---

### Post by DuckHook on 2017-12-11
> **shabidoo said:**
> I looked up cylindar boundaries. Im not sure i entirely understand it but it seems like that might explain the problem?
Cylinder boundaries are not a big deal any more (see [this]("https://ubuntuforums.org/showthread.php?t=1854524&p=11310846#post11310846")). This would not account for your symptoms.

> **deadflowr said:**
> No. Not unless you set a home partition that they all share. ( Or if you tried to get funky and let them all share a system directory or two like the /lib directory, which would be total non-sense if you tried to do that)

Two general questions:

How'd you install cinnamon?

And what version of Ubuntu? (version being 14.04 or 16.04 or 17.10)

It may be as simple as reinstalling the lubuntu-desktop package.
&#8593;&#8593;&#8593;+

@shabidoo: Please answer deadflowr's queries.

---

### Post by shabidoo on 2017-12-11
> **DuckHook said:**
> My bad. Command should be:```
sudo parted -l
```I've also corrected my original post so as not to confuse lurkers.Here are the results of the two commands, I uploaded a pic cause I don't know how to make a hard break with these text boxes. I never installed cinnemon...would prefer it not be installed ever. I have the most recent lubuntu 17.10 . I didn't share partitions (don't even know how to do that) nor would want to.Partition 1 is LXLE. 3 is MXLinux and 4 is Lubuntu 17.10

---

### Post by vasa1 on 2017-12-11
> **shabidoo said:**
> Here are the results of the two commands, I uploaded a pic cause I don't know how to make a hard break with these text boxes. I never installed cinnemon ...
There's no need for a hard break. Just copy the entire output and paste it here between code tags.

Please post the output of *ls /usr/share/xsessions*.

---

### Post by shabidoo on 2017-12-11
Hey. When I put the text between the tags, it doesn't keep any of the formatting. In fact, whatever I type it takes out all hardbreaks completely. I don't know why or how to change that. Here is the results of the other command:>  ls: cannot access xsessions: No such file or directory/usr/share:abiword-3.0	       gnome-vpn-properties	       nvidiaaclocal		       gnupg			       omfacpi-support	       gnupg2			       ontologyadduser		       GraphicsMagick-1.3.20	       openshot-qtakonadi		       groff			       openvpnalarmclock	       grub			       oragealarm-clock-applet     gscan2pdf		       os-proberalsa		       gsmartcontrol		       otsant		       gst-plugins-base		       p11-kitantiX		       gstreamer-0.10		       pacplapache2		       gstreamer-1.0		       pamappdata		       gtk-doc			       pam-configsapplication-registry   gtk-engines		       paroleapplications	       gtkhash			       pavucontrolapport		       gufw			       pcmanfmapps		       gutenprint		       pdfshuffleraptitude	       gvfs			       peg-eapt-xapian-index       hal			       perlaspell		       hardinfo			       perl5audacity	       help			       pixmapsautostart	       hibernate		       pkgconfigavahi		       hplip			       pkg-config-crosswrapperavidemux6	       hunspell			       pnm2ppaawk		       i18n			       polkit-1backgrounds	       icedtea-web		       popplerbase-files	       icons			       ppdbase-passwd	       idl			       pppbash-completion        ImageMagick-6		       projectMbinfmts		       info			       pstoeditblueman		       initramfs-tools		       pulseaudiobroadcom-sta	       inkscape			       pyrenamerbug		       insserv			       pysharedbuild-essential        installation-report	       pythonca-certificates        iptables			       python3ca-certificates-java   java			       python-aptcalendar	       javascript		       python-supportcatfish		       javazi			       qpdfviewcli-common	       kde4			       qt4clocky		       keymaps			       qt5color		       keyrings			       qtchoosercolord		       keyutils			       readlinecommon-licenses        ladspa			       roxconsole		       latex2html		       sambaconsolefonts	       libaudio2		       screenconsole-setup	       libc-bin			       scribusconsoletrans	       libdbi-perl		       seahorsecryptsetup	       libexttextcat		       sgmlcups		       libfm			       sgml-basedbus-1		       libgksu			       sgml-datadebconf		       libgphoto2		       shotwelldebhelper	       liblangtag		       smartmontoolsdebianutils	       libnm-gtk		       smtubedesktop-directories    libquvi-scripts		       snmpdh-python	       librarian		       sopranodict		       libreoffice		       soundsdictionaries-common    libsensors4		       spamassassindirectfb-1.2.10        libthai			       sshdiscover	       lightdm			       ssl-certdisk-manager	       lightdm-gtk-greeter-settings    strigidjvu		       lintian			       sweepdns		       locale			       synapticdnsmasq-base	       luckybackup		       system-config-printerdoc		       lyx			       system-config-sambadoc-base	       m2300w			       systemddotnet		       man			       system-tools-backends-2.0dpkg		       man-db			       sysvinitecryptfs-utils	       maven-repo		       sysv-rcemacs		       mc			       tabsetemesene		       menu			       tcltkemoticons	       metainfo			       templatesenchant		       midori			       terminfoepiphany-browser       mime			       tex-commonevolution-data-server  mime-info		       texlivefarstream	       mimelnk			       texmfFBReader	       mirage			       themesfbxkb		       misc			       Thunarfeh		       mixxx			       tlp-pmffmpeg		       mobile-broadband-provider-info  toolsfile		       modass			       transmissionfile-roller	       mono			       ufwfirefox-esr	       mono-2.0			       upstartfontconfig	       mozilla			       usb_modeswitchfonts		       mx-bootrepair		       vimfonts-droid	       mx-codecs		       virtualboxfoo2qpdl	       mx-defaultlook		       vlcfoo2zjs		       mx-findshares		       volumeicongalculator	       mx-flash			       vpnc-scriptsgalternatives	       mx-installer		       vrmsgames		       mx-menu-editor		       vtegbrowse		       mx-network-assistant	       wallpapersgcc-4.9		       mx-packageinstaller	       webkitgtk-1.0gcj		       mx-packageinstaller-pkglist     webkitgtk-3.0gconf		       mx-remaster		       winffGConf		       mx-remastercc		       X11gcr-3		       mx-repo-manager		       xfburngdb		       mx-select-sound		       xfce4gdebi		       mx-snapshot		       xfce4-mixerGeoIP		       mx-system-sounds		       xfce4-notes-pluginghostscript	       mx-tools			       xfiggimp		       mx-usb-unmounter		       xfwm4git-core	       mx-user			       xgreetersgitweb		       mx-welcome		       xinegksu		       myspell			       xine-libglib-2.0	       mysql			       xmlgmerlin		       mysql-common		       xml-coregmtp		       nano			       xscreensavergnome		       ndisgtk			       xsessionsgnome-control-center   netpbm			       yelpgnome-online-accounts  nfs-common		       yelp-xslgnome-ppp	       nfs-kernel-server	       zlibrarygnome-schedule	       nm-applet		       zoneinfognome-shell	       numpy			       zshI had to use quote because when I use code it just creates one enormous line. I used the terminal on my MXLinux as I cannot get a terminal on the Lubuntu.

---

### Post by deadflowr on 2017-12-11
No, you definitely installed cinnamon.
The question was how, and unfortunately you don't know, or can't remember.
We can say with good measure that it wasn't on purpose.
Water under the bridge at this point.

vasa1's output is a good idea
but the command should be
```
ls /usr/share/xsessions
```
no break between share/and xsessions.

---

### Post by vasa1 on 2017-12-11
> **deadflowr said:**
> ...
vasa1's output is a good idea
but the command should be
```
ls /usr/share/xsessions
```
no break between share/and xsessions.
Sorry about that :(

I'll go back and fix it.

---

### Post by shabidoo on 2017-12-11
> **deadflowr said:**
> No, you definitely installed cinnamon.The question was how, and unfortunately you don't know, or can't remember.We can say with good measure that it wasn't on purpose.Water under the bridge at this point.vasa1's output is a good ideabut the command should be```
ls /usr/share/xsessions
```no break between share/and xsessions.I guess I must have installed it but I don't know how I could have...twice. Maybe it came along with a program I installed, though they were all pretty standard programs (VLC,  QTorrent, Filemanager, Chromium, GIMP, Flash). The only package i installed not in the software centre or synaptic was WPS (kingsoft office suite). I didn't make any other changes to the desktop enviroment other than selecting icon packs and a new wallpaper. I dont even know how to install cinnamon. Here is the results of the command from the terminal in my MXLinux:```
lightdm-xsession.desktop  xfce.desktop
```

---

### Post by DuckHook on 2017-12-11
The command that deadflowr and vasa1 want you to run is useful only if you run it within the problem session. It doesn't give useful info from within MXLinux. However, you've stated that you can't get the problem GUI session going. Therefore, running terminal sessions and reporting them back can prove difficult.

You can get into a command line shell using <Ctrl>+<Alt>+<F1>, run the command that way and record the results to report back, but I believe that you will just end up showing us what we already suspect: that the Cimmamon DE has been installed, possibly alongside the proper Lubuntu stuff. If you want to try this procedure, on my 16.04 VM, the results of the command is:```
duckhook@Lubuntu:~$  ls /usr/share/xsessions
Lubuntu.desktop  Lubuntu-Netbook.desktop  LXDE.desktop  openbox.desktop
```If your output shows anything more than these, you've somehow dragged in an extra DE.

Here's my recommendation: if you are not concerned about the data or apps on your problem install, simply reinstall Lubuntu. This will give you a fresh install without the Cinnamon bits. You've stated that you tried to back out Cinnamon, reinstalled Lubuntu, etc. My concern is that, given what we don't know about your actions, the integrity of your system is now compromised. Rather than trying to hunt down discrepancies, it will probably take less time and aggravation to simply do a pristine Lubuntu install. Then, you should be very careful about what additional apps you install. Some apps may drag in the whole Cinnamon environment unbeknownst to you. If in doubt, check first on these forums.

If you choose this route, make sure you are installing Lubuntu from the main repos. You can torrent a proper image from [here]("http://lubuntu.me/downloads/"). Torrents are more reliable than direct downloads. I would also recommend installing Xenial (16.04) over Artful (17.10). LTS versions are more stable and reliable, especially for new users.

I'm turning in for tonight and will check in on this thread tomorrow.

---

### Post by RobGoss on 2017-12-11
> **shabidoo said:**
> Hi Rob. Thanks for replying. I installed LXLE and MXLinux on different partitions and created a new partition for Lubuntu. Is it possible that conflicts can happen between different distributions on different partitions? I'd prefer to not wipe the whole harddrive and only install lubuntu but would if you think it's a probable solution.


You do not have to wipe the whole hard drive clean, You can use that same partition to install Lubuntu

> Is it possible that conflicts can happen between different distributions on different partitions?

I don't see how that would be possible seeing there on different partitions. If you're running more then one OS on your machines anything you do should not effect another distribution on a different partition

---

### Post by shabidoo on 2017-12-12
Thanks Rob for the detailed reply. I decided in the end to wipe my harddrive and just install Lubutu 16 using the torrent. I did so and while it is even a little faster than 17 on my computer, the video players are sluggish as they were on almost all the other linux distros i tried (on lubuntu 17.10 videos played totally fine). Tomorrow I will install 17.10 on the computer as video watching is important for me. I think its pretty safe to install: VLC, Gimp, flash (available on the software centre) and qbittorrent (available on synaptic).

The only two programs that may have interfered with the op system would be WPS (i need this office suite as openword doesn't keep formatting on some documents) which I downloaded and installed on my own. I also installed icetea and plug in and java webstart (needed to play Go online) which was the last thing I installed both times.  Maybe one of these two packages brought about the cinnemon problems?

---

### Post by vasa1 on 2017-12-12
> **shabidoo said:**
> ...
The only two programs that may have interfered with the op system would be WPS (i need this office suite as openword doesn't keep formatting on some documents) which I downloaded and installed on my own. I also installed icetea and plug in and java webstart (needed to play Go online) which was the last thing I installed both times.  Maybe one of these two packages brought about the cinnemon problems?
It may depend on whether you've installed any package via a ppa. How did you install the packages?
```
grep -i "status installed cinnamon" /var/log/dpkg.log dpkg.log.1
```
If you see something like /var/log/dpkg.log.2.gz, then try
```
zgrep -i "status installed cinnamon" /var/log/dpkg.log.*.gz
```

---

### Post by DuckHook on 2017-12-12
> **shabidoo said:**
> …The only two programs that may have interfered with the op system would be WPS (i need this office suite as openword doesn't keep formatting on some documents) which I downloaded and installed on my own. I also installed icetea and plug in and java webstart (needed to play Go online) which was the last thing I installed both times.  Maybe one of these two packages brought about the cinnemon problems?

> **vasa1 said:**
> It may depend on whether you've installed any package via a ppa. How did you install the packages?[/CODE]
&#8593;&#8593;&#8593;+1

I would suggest that you download WPS directly from their site (**NOT** via PPA) and install that way. Also, I could not help noticing that you refer to the limitations of "openword". I am not familiar with that app, but you may have better luck with Libreoffice which is possibly better at retaining formatting. Libreoffice is in the repos. No harm giving it a try.

WPS site is: [http://wps-community.org/downloads](http://wps-community.org/downloads)

Icedtea is available from the repos and should not drag in anything else:```
sudo apt install icedtea-plugin
```…or for the more recent package:```
sudo apt install icedtea-8-plugin
```

However, if you are using Icedtea, why are you running Java Web Start? Shouldn't you be using Icedtea-Web?

If running Artful (17.10), I believe that you can install the whole ensemble with:```
sudo apt install icedtea-web
```If installing this metapackage, you will not need to install *icedtea-plugin* separately.

---

### Post by DuckHook on 2017-12-13
> **DuckHook said:**
> If running Artful (17.10), I believe that you can install the whole ensemble with:```
sudo apt install icedtea-web
```If installing this metapackage, you will not need to install *icedtea-plugin* separately.
Bad info above. I just checked and Artful does not yet have this package in the repos. Apologies.

You may have to compile it from source. From Launchpad: [https://launchpad.net/ubuntu/+source/icedtea-web](https://launchpad.net/ubuntu/+source/icedtea-web)
From developers' site: [https://icedtea.classpath.org/wiki/IcedTea-Web](https://icedtea.classpath.org/wiki/IcedTea-Web)

Neither should drag in things like Cinnamon.

---

### Post by shabidoo on 2017-12-13
I installed javawebstart so that I can load the KGS Go playing app directly (without a browser). I couldn't do it with just Iced Tea (or at least I couldn't figure out how to do it). As for WPS I downloaded it directly from their website and it was an instant install.

WPS was the only program I installed without using synaptic or the software centre so I had never used the terminal to install anything (the WPS was a .deb package which installed with a few clicks of the mouse).  Should I be installing them via the terminal? I thought via synaptic and software centre it was just safer and would avoid any mistakes. I've never typed "sudo su" before. In fact I hadn't even used the terminal at all the second time I installed lubuntu until the cinnemon disaster happened again.

Libre office is better than open office for sure and while it is close to keeping the MSWord formatting, its not close enough (that is it takes a lot of time to reformat the tiny discrepancies on each and every document). WPS is virtually seamless with MSOffice and on Linux it is add free so I'd definitely prefer it.

Apart from my unusual cinnemon bizarrity...I do really like lubuntu so far.

---

### Post by DuckHook on 2017-12-13
I am beginning to think that you might mean something completely different when you state "Cinnamon Desktop". So far, nothing you are doing would install the Cinnamon DE. Are you, perhaps, confusing something like Lubuntu-Netbook DE or the Openbox DE with Cinnamon? Lubuntu might fall back to these environments if Lubuntu DE can't load. As vasa1 and deadflowr have asked, you really must post the output from:```
ls /usr/share/xsessions
```

Last, but not least, you are mixing apps in a strange way by running Java Web Start with Icedtea. I'm not surprised that it works—after all, Icedtea is supposed to be a replacement for Java—but if people want to run a true Java component, then they usually choose to do so on a true Java environment. Download page: [https://www.java.com/en/](https://www.java.com/en/)

---

### Post by shabidoo on 2017-12-13
This is what I get from the command:

> 
Lubuntu.desktop  Lubuntu-Netbook.desktop  openbox.desktop

I cannot be sure if there really was a switch to cinnemon or not. I was never familiar with it before. Suddenly, my computer loads and the desktop environment has completely changed. It slowed down considerably, the enviroment was much more sophisticated than the original, there was a system tray notice saying something like "Cinnemon may slow down your computer" or something like that. So I assumed the desktop enviroment was now cinnemon. I checked out some screen captures of the two desktop enviroments you mentioned and what I had there looks nothing like those two DEs. It had an elaborate start menu and stylish elegant icons. When I look at some screencaps of cinnemon on google images, it pretty much looks like the sudden DE it was switched to.

In any case, I've found a way to tweak the gnome player and it plays most videos quite well now. As version 16 works much faster and is more responsive than 17, unless there is any good reason not to, I'd like to stick with version 16. I've installed the programs I need and have done the updates, the Go app works perfectly fine. When I try to open the KGS go program (as a jar file) nothing happens when I try to open it with open jdk java runtime. When I install the webstart...it loads and works fine.  So, unless the desktop enviroment suddenly changes again I'm happy to enjoy my fast operating system the way it is now. Or should I go back to 17?

---

### Post by DuckHook on 2017-12-13
> **shabidoo said:**
> T…I'm happy to enjoy my fast operating system the way it is now. Or should I go back to 17?
NO NO. Do ***not*** go to 17.10! If everything is stable for you now and you are happy with things, then stick with Xenial. We are unlikely to be hearing back from you if you stick to Xenial. Not that we don't want to hear from you, but we prefer your presence as a willing participant and not because you have a problem. You will find Xenial more stable and reliable.

Oddly, after this convoluted journey, it seems that you now have a pretty decent system and are reasonably happy with it. Perhaps the Cinnamon episode will always remain a mystery (and best to let sleeping dogs lay). You'll have a story to tell to your grandchildren: "When I first installed Lubuntu…"   :biggrin:

Good Luck and Happy Lubuntu-ing!

---

### Post by shabidoo on 2017-12-14
> **DuckHook said:**
>  Perhaps the Cinnamon episode will always remain a mystery (and best to let sleeping dogs lay). 

Yeah. It's really nice to have a fast desktop for my low spec computer, and the extra bonus is you get most of the advantages of ubuntu (software centre, themes, problem solving etc). You guys were super fast responding and helped me get it going. Thanks a lot!!!!

>   Oddly, after this convoluted journey, it seems that you now have a pretty decent system and are reasonably happy with it.Good Luck and Happy Lubuntu-ing!

I told some of my computer-smart friends about the cinnamon thing and they are equally baffled. Unsolved mystery. Thanks again!!!

---

