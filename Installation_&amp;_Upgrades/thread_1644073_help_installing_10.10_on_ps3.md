---
title: "help installing 10.10 on ps3"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by darckhart on 2010-12-12
i'm having trouble installing the latest ubuntu v10.10 on my ps3 (FW v3.15). i had no trouble installing YDL v6.2 long ago, but since i'm more familiar with ubuntu, i wanted to give that a try. i am using the "alternate version" of the ppc+ps3 iso.

the system gets to the kboot prompt fine, then i press enter, a few lines of something with usb stuff scroll by, then it hangs at this point:

ps3-ehci-driver sb_05: usb bus 1 deregistered

upon where my keybd (ms ergonomic 4000) in port 1 gets turned off. disconnect and replugging keybd does nothing. i'm forced to hard shutdown with the back switch, then hold power button 5 sec to get back into ps3 os.

has anyone gotten this to work? i'm dl the "desktop" version currently to give that a try but i'm not sure how that will go.

edit: ok i got the same error. and here's a pic:
[IMG]http://i56.tinypic.com/2vxnjnd.jpg[/IMG]

---

### Post by cowman on 2011-03-02
Hi, saw this post and I'm having exactly the same problem/error.

Has anyone come up with fix yet?

---

### Post by zoggnoff on 2011-03-29
Same exact problem. I use a Logitech usb keyboard. Not sure why this does not install.

---

### Post by zoggnoff on 2011-03-29
it is definitely **not **the image (verified md5sum) and it is not the media. first, I burned a cheap Sony CD-R. second, I tried a Taiyo Yuden DVD-R with slow speed and verification; same result.

all I can think is the newer Ubuntu must not be compatible with the original large-bodied Forty-Gig Playstation3s or the *otheros.bld* it uses isn't compatible. Either way, I am now downloading _Desktop PPC PS3 version 9.10_ just for the hell of it.

I might, while i'm waiting, download and burn YDL's *otheros.bld* to quench my curiousness. let yall know when i got results. cheers

update: YDL's *otheros.bld* grafting with 10.10 Ubuntu Alternate is a no-go for reentry, i repeat, a no-go for reentry. seriously, it was unsuccessful and I am 'now' burning 9.10 Ubuntu Desktop PPC PS3.

update 2: I got by the deregistered thing using downloaded and burned version of 9.10 Desktop PPC PS3 installation CD therefore I decided to download 10.10 Desktop PPC PS3 to give it a try because maybe i will have more luck than the OP and the 9.10 Desktop went well. i will keep you posted

final update:  Success! Desktop PPC PS3 **9.10** did install. HOWEVER, there are a few caveats; DO NOT LET THE DEFAULT INSTALLATION CHOOSE PARTITIONING OF THE HARDDISK FOR YOU. installing this OS on PS3 takes a very, very long time and you DO NOT want to sit through it twice like I did. by default it will try to do an install of / on ext4 with journaling--this will come back as filing system not found error. CHOOSE EXT3 WITH JOURNALING AND DO NOT TOUCH PS3VRAM, repeat, leave ps3vram alone. What i did was alloted 256 Mb to swap and the rest as ext3 for /

things that don't work as of yet, touchpad. wireless kinda works as in i had to manually force a connection. not sure on how to set it up to automatically connect. any suggestions on how to fix these problems would be appreciated. Good luck and in case you are wondering I did try both the Alternate and Desktop 10.10 versions of PPC PS3 Ubuntu and neither worked. Stick with 9.10.

Peace

residual update: I got the wireless to automatically connect by editing
```
sudo nano /etc/network/interfaces
```Here is what I had to do:

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
pre-up /sbin/ifconfig wlan0 up
wireless-key YOUR_HEX_PASSWORD_FOR_WEP_HERE
wireless-essid YOUR_NETWORK_NAME_HERE
post-up /sbin/dhclient wlan0

```you will have to replace what is capitalized with your own information.
If you use WPA for security all I will say is that you have to nano /etc/wpa_supplicant.conf and then add a call to it in your /etc/network/interfaces which i am not going to discuss because i do not use WPA so good luck with that
but if you are unsure what your info looks like, do this
```
sudo iwlist wlan0 scanning
```I still can't use the friggen fargen touchpad
also, i did sudo apt-get ubuntu-restricted-extras
but use at your own discretion because this ruined my sound so i purged it

touchpad update: resolved. it is a conflict with another package, the solution is to remove or purge it (THE FOLLOWING IS ONLY FOR KARMIC 9.10 NOT NATTY 11.04; nor any other ubuntu release)

```
sudo apt-get purge xserver-xorg-input-synaptics
```My next white whale shall be to utilize the ps3vram and get the multimedia issues fixed. it turns out that while adobe does make a flash player for linux, it does not support PowerPC so i386 architecture only--bummer. I tried firefox plugins gnash and swfdec but they did not solve it. i will let yall know.

REUPDATE:  i have got a nice little reward for you. add ps3vram to swap.

first do this:
```
sudo nano /etc/modules
```at the end of this file add this line:
```
ps3vram
```save and then do this
```
sudo nano /etc/rc.local
```MAKE THE LAST THREE LINES LOOK LIKE THIS, IN THIS ORDER:[FONT=monospace]
[/FONT]```
mkswap -f /dev/ps3vram
swapon -p 10 /dev/ps3vram
exit 0
```[FONT=monospace]
save and reboot. to see if it is working after you reboot issue the following:
[/FONT]```
swapon -s
```[FONT=monospace]

streaming video update: (PLEASE DO NOT USE THE FOLLOWING TWO LINKS--INSTEAD PAGE-DOWN MUCH FARTHER TO MY OTHER POST; THE POST WITH THE THUMBNAIL IMAGE)
I have had some luck streaming online content from loombo and movshare by utilizing the following two links:
[/FONT][https://addons.mozilla.org/en-US/firefox/addon/748](https://addons.mozilla.org/en-US/firefox/addon/748)
[http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)
also: 
```
sudo apt-get install totem-gstreamer totem-plugins
``` BUT DO USE THIS **^**

supplementary update: I have some weird issues with connecting to wifi therefore i added */sbin/dhclient wlan0* to System>Preferences>Startup Applications. also, after I did a software update via System>Administration>Update Manager firefox stayed in offline mode all the time so I had to punch up *about:config* in the firefox location (where the http www yadda yadda stuff goes) then put *toolkit.networkmanager.disable* in the filter and double click to set **true**.

---

### Post by zoggnoff on 2011-04-01
I can confirm that 10.04 Desktop PPC PS3 works too. If you download 11.04 however, only download the alternate or possibly the server edition of ppc but please note that the iso for ppc ps3 is not available (yet?). i did install 11.04 via the Alternate PPC available but the installer would not connect to my network and when i tried to manually set it in *execute shell* it still would not issue an ip (why this requires network connection i may never know). although to be honest, one thing i should have tried is to set the /etc/network/interfaces like i did before but even if it had connected--the installer would not. therefore what you wind up having is a command prompt and no installed packages which some might prefer but i personally would be lost in the middle of the ocean, so to speak, added to that the screen resolution was that of 4:3 rather than my native 16:3 (probably due to it not being a PS3 release specifically which i would hope you could apt-get ps3videomode to fix) anyway it is your choice if you wish to try it. one more word of advice, even if you do try it and you do want the server edition, get the alternate edition, it has both options built in plus a slew of other ways to install.

(DO NOT USE XFS FILING SYSTEM) the xfs filing system works on the 11.04 non-ps3 edition of ppc yet hangs on all the other true-ps3 editions, don't ask me why.  (IT ONLY WORKED ON THE BASE SYSTEM)

also the alternate 11.04 ppc image _does not_ include *otheros.bld *so you will have to use one of the other discs for the preliminary *install other os* action in *system settings* of the XMB Sony Playstation operating system, without that *otheros.bld* you have no kboot to run the installation. (If you decide to get an *otheros.bld* file and put that on to a pen drive or some other media you will have to mirror the path of how it is on the installation cds, i.e. C:\PS3\otheros\otheros.bld because this is the only place XMB will look for it on your chosen media)

and i'm now using ex2 instead of ext3 because it is said to be faster, less reliable, but faster. i may go with fluxbox over gnome, still not sure though. i think a lot of this speed tweaking in linux is negligible, especially file system speeds.

irssi ftw

note: on the 11.04 you will want to use your _tab key_ to get to a ppc64 install option as the ps3 is ppc64 not ppc, anything else will cause the machine to gak, shut off and blink

i've already wasted a ton of time on this but i really want that 11.04 so i think later today i am going to work on that, my new plan would be to make the install with my cable modem connected directly to my machine which i have no idea why i didn't think about doing earlier just that i was possibly too tired to think. hopefully with a proper install the wifi fixes itself. i will keep at it

awesome update: I found a procedure on how to upgrade from 10.04 to 10.10 located at [https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)
I will let you know how it goes

Wow I had no idea it would be this easy to upgrade from 10.04 to 10.10.
Here is what i think you should do to get the latest ubuntu on your playstation, download and burn three images. (not as a data disc, as an extracted iso disc with all the folders and stuff on it like one would do in imgburn under write mode not build mode, i.e. write image to disc)
1. 10.04 desktop ppc ps3
2. 10.10 alternate ppc ps3
3. 11.04 alternate ppc
when you have 10.04 installed, all you have to do is load the next disc into the drive and ubuntu will upgrade to 10.10 for you. remember to remove the disc when it reboots, i left mine in and thought i was having the deregistered crap again but i was wrong, just had to remove the disc and i am on 10.10 right now.
i'm now going to put the 11.04 alternate ppc into the drive and hope for the best. (the last two discs have to be alternate and the first has to be desktop for this to work)

also note that 10.04 is a LTS and one can not go from that to 11.04 directly or so i am so told.

another update: i was wrong about loading the 11.04, it did not automatically upgrade and all attempts to mount the cd-rom and issue commands to force an upgrade came back with errors and would not allow an upgrade, even trying upgrade-manager was a total bust with normal upgrades set in the settings (i tried every way in which to get this method to work, it did not work. it was a waste of time). I have not figured what went wrong but i am determined to get 11.04 so i will work on it some more. there is however a huge difference in performance using fluxbox over gnome. it is the best and fast as hell. i was going to abandon firefox in lew of speed but using fluxbox improved the speed like 5 times faster of every app. i hate gnome  :D.

```
sudo apt-get install fluxbox
```then just choose it at the bottom before you sign in to the GUI from the login screen. it should default to fluxbox after the first use.

more goodies
do this:
```
sudo nano /etc/apt/sources.list
```add these
```
deb http://www.debian-multimedia.org/ lenny main 
deb-src http://www.debian-multimedia.org/ lenny main 

deb ftp://ftp.debian-multimedia.org/ lenny main 
deb-src ftp://ftp.debian-multimedia.org/ lenny main
```save, close and then do this
```
sudo apt-get update
```and then do this
```
sudo apt-get install libdvdcss2
```and this
```
sudo apt-get install clive mplayer
```

**I forgot to tell you that you will need a public key for some of these repositories** but that is okay we can fix that. the process is simple when you get the hang of it. we first figure out what key number they are looking for and to do this simply update and read what is at the bottom:
```
sudo apt-get update
```
record the key number and do the following using the actual key number:
```
gpg --keyserver pgpkeys.mit.edu --recv KEYNUMBERHERE
```
this ought to say something about loading 1 key and then do:
```
gpg --export --armor KEYNUMBERHERE | sudo apt-key add -
```
and of course update again
```
sudo apt-get update
```

---

### Post by zoggnoff on 2011-04-03
Guess what

mike@ps3:~$ ```
cat /etc/issue
```Ubuntu natty (development branch) \n \l

That's what.

I just did a clean, fresh, direct install of 11.04 Natty Narwhal Ubuntu on Playstation 3 via the Alternate PPC image and success it works!
by the way Ps3 is no longer supported which makes this ridiculously funny.
but as long as Ubuntu supports ppc64 i'm good, you're good. everybody poops :D

the screen is awesome
visually great.
the trick was that i abandoned wifi and hooked straight into the machine,
install went like a charm. a few caveats though

you will need a disc with otheros.bld on it. the, i think, 3.15 or earlier or hacked ps3 firmware--whichever allows you to put linux on ps3 (obvious) and the alternate ppc disc you will need so download all that.

do not do guided partition, do not set boot flags, do not pick anything other than ext2 or ext3 as your / and do not touch ps3vram.
my partition went like this, both being primary not logical.
```

ps3da1     /     ext2      26.0 Gb    (exact)
ps3da2           swap    800 Mb     (estimated)
```the installer does not always issue an ip which you will need, but 3 out 4 times it did issue one off the bat when i hooked the ethernet cable directly to the back of the ps3.

write this down
```
ports.ubuntu.com
```you will need this for when it asks you for a mirror during the packages thing
next it will ask you for a sub directory but just leave it as /ubuntu-ports/
you don't need to write that down, it's default

okay so that is about all you really need to know unless the installer does not give you an ip you can go to the main screen and "execute shell" then do this AFTER YOU INSTALL THE BASE SYSTEM BUT BEFORE THE PACKAGES you will need a connection
```
/target/sbin/ifconfig eth0 up
```and then
```
/target/sbin/dhclient eth0
```if you try it before installing the base system it will come up as not found, i think

first impressions:
i turned off all the startup applications on the default GUI and it is a bit faster plus i am using the 'classic without effects' mode of Gnome. so far so good. i may still go with fluxbox. it needs a lot of tweeking for multimedia. dvds load and ask me what to do but don't actually play or find a suitable plugin so that is annoying.

this was the first thing i added to my box when i got it running
```
sudo apt-get install ps3-utils
```i think this gives you the ps3videomode package, not sure, it might have been included, who knows.
to use it in full screen 720p do **sudo ps3videomode -m 3 -f**
ps3videomode -m will give a list of other options and the -f is the full screen setting
incidentally you may also want to set full screen mode by editing your /etc/kboot.conf
what you do is put **video=ps3fb:mode:131** for 720p which means 3+128 so whatever your resolution is add 128 to that. careful not to place this in the wrong spot.
i will show you mine for your reference

my kboot.conf
```
message=/etc/kboot.msg
default=linux
timeout=1
linux='/boot/vmlinux initrd=/boot/initrd.img root=/dev/ps3da1 video=ps3fb:mode:131 quiet'
old='/boot/vmlinux.old initrd=/boot/initrd.img.old root=/dev/ps3da1 video=ps3fb:mode:131 quiet'
```

---

### Post by charlieluna on 2011-04-03
> **cowman said:**
> Hi, saw this post and I'm having exactly the same problem/error.

Has anyone come up with fix yet?

you can't install another operating system on the PS3 now. sorry. it was in update 3.54 or 3.55 i think. 

I have a PS3 that's why I know this.

And why would you want to screw with something that isn't broken? The PS3 OS works just fine.

---

### Post by zoggnoff on 2011-04-04
> **charlieluna said:**
> you can't install another operating system on the PS3 now. sorry. it was in update 3.54 or 3.55 i think. 

I have a PS3 that's why I know this.

And why would you want to screw with something that isn't broken? The PS3 OS works just fine.

Sony did do that but there are ways around it, i.e. modified firmware, reverting to older firmware or perhaps he read that the new firmware would remove otheros and have been avoiding instituting an update. personally if not for its Linux capability i would never use this. i am on 11.04 ubuntu on my ps3 right now watching a DVD, chatting on IRC, editing commands in the terminal and have firefox going with a few webpages on Fluxbox. it is ridiculously fast and you can not do all that at the same time from the XMB. i may never use my laptop again. so to each his own. there are people in the ubuntu chats with myriads of problems concerning hardware yet this little powerpc64 is a champ and has no problem doing the hard work. i got bluetooth, weather updates, plug n play works. it is amazing what this can do. 

i have an external burner with usb which i have yet to test but i am fairly confident when i do i can use this to create discs, so rock on

before when i had YDL i used this to run a .com. granted i had to use a free dynamic dns service. makes a great server. runs apache. everything you could dream of doing on linux is possible with PowerPC64 running Ubuntu. XMB is not that versatile though it is awesome

**UPDATE!!!! YOUTUBE WORKS:**
```
sudo apt-get install gnash mozilla-plugin-gnash gnash-cygnal gnash-tools

```if for some reason that does not work, the first thing i did was downloaded this [http://ftp.gnu.org/gnu/gnash/0.8.9/gnash-0.8.9.tar.gz](http://ftp.gnu.org/gnu/gnash/0.8.9/gnash-0.8.9.tar.gz) uncompress it in any directory, *cd* to that dir and do *./configure* (with the period in front of the slash)
this configures a list of stuff and then at the end of this were a lot of suggested and needed dependencies for me to "apt-get install" i installed every single one under titles "WARNING" and "RECOMMENDED." (you may not need to do any of this). after *./configure* and all the *apt-get installs* i did *make* and then after that i did *make install*. the app did not show up in the plugins so i did the code above this paragraph and youtube worked! success!

**web browser SPEEDINESS:**
```
sudo apt-get install midori
```
this web browser is so god damn fast you would have to be lightning to catch it. (note: i tried seamonkey, opera, arora, konqueror, dillo, w3m, lynx, elinks) as far as capability goes and speed i would say this would be the next best thing to google chromium (chromium does not have a ppc candidate). added to that there is a sweet *speed dial* which is totally awesome and convenient. midori does youtube. myspace shows up better in midori than it does in firefox (thumbnails will not load in mypace using midori). facebook defaults to the mobile website but if you just bookmark/speed-dial [http://www.facebook.com/home.php](http://www.facebook.com/home.php) you will circumvent that. (annoyances about it: some of the other videos that load in firefox won't load in this but then megavideo works better in this so it is literally a mixed bag of results. the passwords for login sites are not saved.) I would say inbetween midori and firefox seamonkey is good but still no where near as fast as midori. it is your choice. but i can literally have fifteen tabs open in midori and you would not know it) I HATE THE duckduckgo default quick search at the top but whatever i can live with that for a while. maybe someone knows how to swap it out?

**about dillo:**
I wanted to get behind dillo and use it as my all-time browser. dillo is **fast** but is also very much a dimly-lit mostly-stripped knocked-down skeleton of what i am calling the more desired content-rich action-smooth web browser. this just did not have enough sparkle for me, and i gotta have more sparkle. it is a text-like browser that is way more content rich than the likes of lynx, w3m or elinks. and choosing it over them you can not go wrong. HOWEVER, if you enjoy content  as much as the next guy or gal stick with midori. (if you do it up dillo style you will have to get fltk 2.0 uncompressed, configured and installed then do the same for dillo. also, edit */etc/X11/fluxbox/fluxbox-menu* to add the execute order to launch it from GUI. do *whereis dillo* to find the path so you know what to put. and make a copy of your fluxbox-menu, this thing reverted on me more than once. if you edit this try *ctrl+w* you can then input 'web browser' for a quick search within that document). i am going to go out on a limb and say if you like to read only wiki articles get dillo--it will not make you throw up like those other all-text browsers do but do configure it because at default the text is small.

**DVD encryption:**
i was able to beat the dvd encrypted error by following the tutorials online HOWEVER only with my external usb dvd writer did this actually work, the internal blu-ray dvd-rom must have some very screwed up programing because i noticed i could play DIE HARD 1 on my external and access all of the disc but then on the internal i could only access the extras and non-encrypted pieces but not one VOB would play off the DVD Video disc in the blu-ray drive nor could i even *cp* them which tells me that there is nothing out there as far as fixes go and i tried to change the region with regionset but that errored.

add this to your *Enable blocklist* of **Transmission Bittorrent** and click update
```
http://list.iblocklist.com/?list=bt_level1
```
you can find this yummy snack by right-clicking the fluxbox desktop and then Applications>Network>File Transfer
once in Transmission go into *preferences* and then to *privacy* to add the url

[SIZE=1]thumbnail: thanks, i did not know how to do it small (i misspelled my IRC handle, go figure)
[/SIZE]

---

### Post by hulme22 on 2011-04-06
@ Zoggnoff,
                   Via  google your thread led me here,  hence l registered for your view and you online now , one question how  do l get the right resolution for my tv after logging in via wonderful  petitboot  ([http://www.kernel.org/pub/linux/kernel/people/geoff/cell/ps3-petitboot/](http://www.kernel.org/pub/linux/kernel/people/geoff/cell/ps3-petitboot/))  but default is 720 and my tv is 1080i.Pls help

---

### Post by zoggnoff on 2011-04-06
> **hulme22 said:**
> @ Zoggnoff,
                   Via  google your thread led me here,  hence l registered for your view and you online now , one question how  do l get the right resolution for my tv after logging in via wonderful  petitboot  ([http://www.kernel.org/pub/linux/kernel/people/geoff/cell/ps3-petitboot/](http://www.kernel.org/pub/linux/kernel/people/geoff/cell/ps3-petitboot/))  but default is 720 and my tv is 1080i.Pls help

```
sudo ps3videomode -m 4 -f
```you will need the ps3-utils package *if* you do not all ready have them *yum* them ;) (assuming you are on yellow dog linux) the -f denotes full screen, page-up to see how to add this at boot

---

### Post by hulme22 on 2011-04-06
U true dawg! Prompt reply, Ta. Used to have YDL, then one day, PS3 failed with hard drive is corrupted blah blah blah, luckily enough was one of the saddoes that refuse to upgrade knowing what it will do to my PS3, so got all back on 3.15 hence the search for OS and obviously last YDL was 6.2 so l`m trying Ubuntu and hence the issues and please forgive me, l`m from the dark side (Microsoft) my initial training was in unix, but like l said now on the dark side, hence my ignorance, ah the package that is what i need.Merci.

---

### Post by zoggnoff on 2011-04-06
to any person undecided or contemplating an attempt to install please be well informed:

Natty Narwhal 11.04 as of April 6th 2011 is beta. it is not now nor will it be a long-term support or LTS release.
The 'current stable' is Maverick Meerkat 10.10.
Natty goes stable on April 28th


*LTS duration:  three years. (five years for server) Ubuntu Lucid Lynx **10.04 is LTS***

---

### Post by hulme22 on 2011-04-06
@ Zoggnoff,
                     Thank you, all working ok.

---

### Post by zoggnoff on 2011-04-14
new update: well it has been a while since i posted anything new to this thread and in hindsight i probably should have created my own thread but i just wanted to share with you a new development in my world. I discovered i could put Fedora 12 on ps3 so that is what I did. it took some doing. i had to use the petitboot from kernel.org to install and when it rebooted it pointed at the **wrong /dev/sda1** device but a simple edit in petitboot by pressing *e* let me rearrange the tags. i changed them permanently in */boot/etc/yaboot.conf* so now it boots in fullscreen *video=ps3fb:mode:131* with the proper /*dev/ps3da* location set in yaboot. a simple edit of /*etc/sysconfig/network-scripts/ifcfg-eth0* to set *ONBOOT* to equal *y* instead of *no* got the internet going after reboot and editing */etc/rc.local* like i did before got */dev/ps3vram* activated as swap. I had to *yum* a lot of packages as the system was pretty blank. also, i had to *yum remove synaptics* to get the touchpad/mouse working. the only window manager that would run was XFCE and the gnash plugin is different in Fedora, it is *yum install gnash-plugin*. first thing to do in Fedora was to *yum groupinstall Base* and go through the list of groupinstalls by doing *yum -y grouplist* then *yum groupinstall 'Whatever The Name of the Group is'* then i also created a hashed password in *openssl passwd* then i did *useradd -p MYHASHEDPASS mike* to add a regular user, then *visudo* to add *mike* to the sudoers file under where it said ROOT ALL etc. etc. mirroring the *root* entry but using *mike* instead of *root* of course.
 
took some doing but i managed to get it all working. i downloaded fedora 12 ppc dvd iso in Ubuntu and burned it in Ubuntu using Brasero so that was awesome because that was a first for me.
 
not having fluxbox is kind of terrible.
 
I do not actually intend on keeping Fedora or intend on talking about it but my actual goal with having Fedora is to compile Red Hat Enterprise Linux from source-code using the SRPMs so that i can have that and possibly do a CentOS-like release of my own. the CentOS team do not have access to PowerPC64 so with less people using this architecture and more developers and open source projects dropping out it is up to me to figure a way to do it. CentOS for all that do not know is actually RHEL's compiled source code with various copyrighted images and possibly some of the non-free packages removed. Community ENTerprise Operating System is the most used production server in the world because it is free, available in binary and compiled from Red Hat Enterprise Linux which is software you can compile from source yourself but can not obtain binaries of without paying a support fee to license that support. the purpose would be to use RHEL to cram for a Red Hat Certified Engineer exam which from what i understand is a lengthy test and a certification that pays to have under one's belt. not that one can not make a living using Ubuntu as a production server but it seems that people are more apt to use CentOS, Debian, Fedora, Suse or RHEL for these tasks than they are to use Ubuntu though as a user-friendly desktop replacement built on the same technology as the aforementioned distributions Ubuntu is one of the greatest additions ever pioneered.
 
i realise this was not a ubuntu topic. i apologise and feel free to gripe at me but i had to get it off my chest
 
 
**SCREENSHOT OF FEDORA 12 PPC ON PS3**[URL="http://oi51.tinypic.com/1gke3k.jpg"]
http://oi51.tinypic.com/1gke3k.jpg[/URL]
 
_
_
 
update1: i eventually did get fluxbox to run with *startx* at the command line by first passing *echo "exec startfluxbox" > ~/.xinitrc* on the command line. to boot into it i am told that one would have to edit */etc/inittab* changing the runlevel to *5*, e.g. *id:5:initdefault:* I was however, not able to get the sound to work properly even though it would play when i switched between terminals, i.e. when the GUI was unattended.
 
reupdate: I decided to scrap the install and reinstall via VNC. (Fedora did not originally give me a graphical installer because PS3 simply does not have enough RAM to run it by itself. i am told anaconda's text based installer leaves out a lot of packages which explains why i was left with what felt like a partial Operating System.) it was pretty straight forward. i edited the *arg* in petitboot placing *vnc video=720p ps3fb=4M ro* there and then i opened port *1* of the PS3's ip by calling up the router's gateway ip in a web browser adding the port under the *gaming & applications* heading. i installed TightVNC Viewer on my Win XP machine which i used to connect to my PS3 manually via *192.168.1.103:1*. i am still running the install so i can not comment on how it went; so far so good. i added rpmfusion-free and rpmfusion-nonfree to the repositories during install as to build a more complete dependency tree, the urls for that are *[http://download1.rpmfusion.org/free/fedora/releases/12/Everything/ppc64/os/](http://download1.rpmfusion.org/free/fedora/releases/12/Everything/ppc64/os/)* and *[http://download1.rpmfusion.org/nonfree/fedora/releases/12/Everything/ppc64/os/](http://download1.rpmfusion.org/nonfree/fedora/releases/12/Everything/ppc64/os/)* (also, I may not build RHEL from source afterall but I have not made up my mind to do it or not. Red Hat provides an evaluation binary that is updatable for 30 days so i may just wind up using that and they do support PPC. also, i found that Red Hat serves a beta of version 6 for PPC on the main ftp of their domain in DVD ISO form.) there is a graphical petitboot out there some place that i will most likely install once i have everything configured. i have been keeping a copy of the text based petitboot on external usb and loading it into XMB that way. i hope adding a different version of petitboot will not affect my installation--i am confident it will not.

another update: Well the installation went fine, here is a screenshot post install [http://oi55.tinypic.com/2v0hczs.jpg](http://oi55.tinypic.com/2v0hczs.jpg) and the sound works out of the box as did the mouse but the video has a blue smurf effect that no output video mode changing seems to fix. I am glad to say i picked up another trick to using linux on PS3, if you add *KEYBOARDTYPE=pc KEYTABLE=us* to the arguments in *yaboot.conf* where *quiet* or *ro* and *video=ps3fb:mode:131* is--the cursor comes alive in terminal which might explain why i did not need to *yum remove synaptics* to get the touchpad working in the GUI this last time.

blue smurf update: i have no idea why or what makes this work when vlc would not work but if you *install mplayer* and then *mplayer -vo sdl filename.avi *it just works perfectly and then you hit *f* to go fullscreen. works a treat and no blue tint. subsequently you may have to bring pulseaudio up by *start-pulseaudio-x11 *and then add *-ao pulse* to the mplayer command, e.g. *mplayer -vo sdl -ao pulse filename.avi* of course you will need to have a lot of the gstreamer packages installed and i am using alt+f2 religiously to launch applications in fluxbox, it works a lot like a gnome-terminal without leaving all that onscreen data spooling about.

graphical petitboot update: do not use it. it is not worth the hassle and it does not work right. it has no ps3-bl-option to change resolutions and in 480p mode it was simply unusable. although, i will say petitboot should probably be used over kboot everytime because **petitboot supports ext4** and kboot does not. 


Another screenshot: [http://oi56.tinypic.com/sglstl.jpg](http://oi56.tinypic.com/sglstl.jpg) as you can see i favor firefox's download manager so firefox gets used. midori is faster but it lacks a graphical download manager. which is not so terrible but with firefox i can pause and restart downloads. for large files it is a necessity.

command of interest: brasero crapped out a coaster so i decided to look into burning an image to dvd from the command line so i did *growisofs -dvd-compat -Z /dev/cdrom1=RHEL6.0-20100414.0-AP-ppc64-DVD1.iso* and it worked.

RHEL binaries update: neither 5.6 or beta 6.0 would load the installation so i will be compiling RHEL Server 6.0 from source-code on my own.

---

### Post by hirofujira on 2011-04-15
hi, I'm compiling a new version of kernel, and I was wondering what is the recommended size for ps3fb (aka PS3 GUI framebuffer) ?

Additional info on installing Ubuntu:
 If you **still have problems installing 10.04** **with Desktop Edition**, use the **alternate CD**. That's how I was able to install Ubuntu 10.04 on my PS3.

---

### Post by zoggnoff on 2011-06-20
wow you guys.. i discovered lubuntu-desktop and man is it fast.

what i did was installed ubuntu server with no extra packages and then


```
sudo aptitude install lubuntu-desktop
```when you restart the server, at the login screen, before you enter your username and password choose **LXDE** in the drop down menu on the bottom left.


my next mission will be to scrap this install of ubuntu server and run the lastest mini.iso [http://ports.ubuntu.com/dists/oneiric/main/installer-powerpc/current/images/powerpc64/netboot/mini.iso](http://ports.ubuntu.com/dists/oneiric/main/installer-powerpc/current/images/powerpc64/netboot/mini.iso) for an even leaner version of this but FYI no matter what flavor of ubuntu you have--if you install lubuntu-desktop and choose **LXDE** and have */dev/ps3vram* in your *mkswap* and *swapon* you will see a huge difference in speed.


even video plays better and the cpu cycles aren't all over the place and peaking like they were in the other desktop managers.. this method uses **lxdm** in conjunction with **LXDE** to give you a very fast OS.


i keep drifting between midori web browser and firefox and i suspect that using the package manager to install these provides one with not the latest release of these applications which is probably why i am continuely having to use firefox for some tasks. i have yet to successfully compile chromium web browser, i need to resolve that soon. the only way to get current versions of gnash and midori is to compile and set the new paths and configurations yourself. one caveat about chromium--i have read that it is not faster than midori though i'd rather use it as opposed to firefox so this is essential to me.. also i have picked up a new handy command that helps before attempting to compile the latest application of these things. 

the command is for example for building the latest midori:

```
sudo aptitude build-dep midori
```


i will be trying a few tweaks and will give a run down on how and what i use.. new updates soon

---

