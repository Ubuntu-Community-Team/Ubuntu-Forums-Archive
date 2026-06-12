---
title: "Ubuntu 10.04 First Impressions"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by CrusaderAD on 2010-03-21
First things first, I love the new themes. Even though the "new" icons didn't replace that many, it looks great. I especially like the new Empathy look. Big improvement.

The Gwibber Broadcast abilities are pretty cool. It's neat to tap into these social networks in different ways. Needs more features, but it works nicely.

The overall loading of the operating system is quick, but I'm not impressed with the load time from login screen to desktop, seems slow... but it could be a result of my older hardware.

The new capability with nvidia doesn't impress me... I do have an older card, so it seems like when they try to support new stuff, old stuff breaks. It makes it tough for those guys who don't feel like upgrading constantly.

I have yet to try the supposed iPod compatibility, could be cool... for any music or storage device like it.

Overall, it's awesome. The new look and feel is excellent. The system runs really smooth for a beta release. They're definitely perfecting the technology they implemented in 9.04. Great job. Still my favorite Operating System.

---

### Post by juancarlospaco on 2010-03-21
Gwibber 2 needs a Netbook mode or mini mode, the GUI can be too big for Netbooks, maybe a hack to use smaller icons.

Evolution needs Small Icons option too.

I hope empathy can do Video and file transfer for Final version, whatever i use Gmail.

The rest is simply perfect.

---

### Post by njsharp on 2010-03-21
I've jus installed 10.04 beta 1 in the usual way.  Initial points.

It took me one go to realise that you had to hit a key to get a menu, else it went ahead and did "try without installing".

Maybe its my bad or the hw's fault, but booting from the CD, hitting a key to get the menu, and choosing Install just did "try without installing" anyway, as did  "try without installing" too (I wondered if they had got reversed!).  Hmmph!  Anyway, then I chose the install icon and off it went in the expected way.

I'm very happy for it to look on the Internet for a time server.  However, later in the install it is clearly going back to the Internet to get some files from a repository.  I didn't wireshark my internet connection, so I don't know where it went but I'd bet it was exactly as per /etc/apt/sources.list

Hmmm, it pulled 28Mb.  I'd rather it had waited till it had rebooted from HD and I had time to edit /etc/apt/sources.list to put in my ISP's mirror details, so the download didn't count to my monthly limit.  OK, that's 12Gb so no big deal, but it's not good on principle.

Alpha 3 looked good, so I am hoping I like beta 1 even more.  More later perhaps!

---

### Post by switch10 on 2010-03-21
I don't like that the close, minimize, maximize buttons have moved.  It would take a while to get used to that.  The themes look good other than that.  

I think personally, I will be sticking with 9.10 on my computers, because it works great for me.  The improvements made in 10.04 seem trivial.  I can already sync my IPhone, and if I wanted Gwibber, I could install it.

---

### Post by njsharp on 2010-03-21
Dear switch10

have a read of the buttons<left rationale as so far explained by Mark Shuttleworth:
[http://www.omgubuntu.co.uk/2010/03/mark-shuttleworth-explains-why-window.html](http://www.omgubuntu.co.uk/2010/03/mark-shuttleworth-explains-why-window.html)

As an occasional OSX user, I reckon it won't take long to get used to left.

cheers

---

### Post by Crunchy the Headcrab on 2010-03-21
The button thing is really easy to fix using gconf-editor.  If you would like an explanation, I'd be willing to offer one.  I'm really digging 10.4, especially since the new version of AWN is in the repos!

---

### Post by Uncle Spellbinder on 2010-03-21
I'm finding Lucid to be as stable as Karmic, if not more so. Not crazy about buttons on the left, but easily changeable via Ubuntu Tweak. Everything works great, video is crisp and clear, sound is perfect, no issues with Internet. Just a fine OS so far. And we're still in Beta. 

Love it!

;)

---

### Post by ex-wirecutter on 2010-03-22
I've just done a quick try out of 10.04 beta and I think it's great! So far everything 
" just works " , can't wait for the final release .

---

### Post by switch10 on 2010-03-22
no thanks guys.  I could fix it if I cared to.  I am sticking with 9.10 for many reasons..

---

### Post by Glugglug on 2010-03-22
I just get a silent startup  audio works on everything else .

Nvidia card  activated but not in use .

---

### Post by zeroseven0183 on 2010-03-22
I wanted to execute Operation CWAL already but I still have to wait till  the official release. But so far, I find Lucid Lynx stunningly beautiful and furiously fast. It really works out of the box.

> **Crunchy the Headcrab said:**
> The button thing is really easy to fix using gconf-editor.  If you would like an explanation, I'd be willing to offer one.

I easily managed to switch the buttons to the right (although it's not actually an issue for me). Thanks to this [Python script]("http://eftimie.ro/store/window_controls.py")

---

### Post by ubername on 2010-03-22
My biggest problem is that I get slower internet on Lucid compared with Karmic (a lot - the speedtest results are a bit misleading in that once it gets a connection it seems a bit more happy, but still slow. Day to day browsing, downloading updates etc. seems to be more like a fifth the speed or worse).
[http://ubuntuforums.org/showthread.php?t=1434732](http://ubuntuforums.org/showthread.php?t=1434732)

Other than that I think it is great. One good thing is that reinstalling users from a previous /home partition is now much easier - you just add the user's name and if there is already a directory in /home it just picks it up (in the past you had to do all sorts of tricks). That said, I am not sure why the installer can't just find them anyway - it can find Windows users! (but I haven't tested copying them over.)

---

### Post by coolbrook on 2010-03-22
- It's quick to boot and shutdown.
- Nvidia was detected and files were available through the restricted drivers.
- The minimize/maximize close window buttons are on the left of the title bars.
- It's purple.

---

### Post by njsharp on 2010-03-22
Various folk have referred to changing the buttons back to the right.  I'll not bother myself, but its do-able with gconf-editor key /apps/metacity/general/button_layout and follow the instructions in the Key Documentation when you get there. I think you might want:

menu:minimize,maximize,close

I did try starting an install on different hardware (a tower instead of a laptop) and this time 'Install' behaved properly instead of just like 'Try without installing'.  Repeating on the laptop got the problem again though, so it seems like a hardware based issue.

Both attempts did issue three enigmatic error messages:

init: ureadahead-other main process (1038) terminated with status 4
init: ureadahead-other main process (1039) terminated with status 4
init: ureadahead-other main process (1040) terminated with status 4

Also got a crash report:
Sorry, the program "gvfs-gdu-volume-monitor" closed unexpectedly.

---

### Post by skbhat03 on 2010-03-23
Even i am getting the same crash report gvfs-gdu-volume-monitor closed unexpectedly

But not able to report it correctly :(

---

### Post by sugarland2k on 2010-03-23
I'm using Ubuntu 10.04 UNR (Ubuntu Netbook Release) on my Dell Mini 9 and I love it so far.  Lucid will be a great long term support release.  Thanks to all the developers, testers and the team! :P

---

### Post by njsharp on 2010-03-23
Small point re buttons moving left.

I prefer:

gconf-editor: apps/metacity/general/button_layout

close,minimise,maximise:

so that:
a) it is compatible with OS X (red/yellow/green)
b) as you come up and left from the middle of an open window, you get first to maximise, then minimise and finally close

With close as the rightmost I find myself accidentally closing when I meant to minimise.

Your choice though with gconf-editor

---

### Post by njsharp on 2010-03-23
OOps...
gconf-editor: apps/metacity/general/button_layout

close,minimise,maximise:
better:
close,minimize,maximize:

Damn Yankees!

---

### Post by kansasnoob on 2010-03-23
I've been testing Lucid since the toolchain first came down and I must say it's going downhill!

What looked very promising to begin with now looks like ............ uh, not so good :p

Honestly, what looked great now treats my hardware like crap!

---

### Post by CrusaderAD on 2010-03-29
> **njsharp said:**
> OOps...
gconf-editor: apps/metacity/general/button_layout

close,minimise,maximise:
better:
close,minimize,maximize:

Damn Yankees!

Thanks for posting this! So much better!

---

### Post by king.pest on 2010-03-29
Hey, did anyone of you tried doing update-manager -d upgrade rather than a clean 10.04 install? Did you encounter any problems?

---

### Post by florus on 2010-03-29
I did upgrade-manager -d and had a couple of error messages during upgrade. One about network applet and one about open office. Both work fine and after a couple of boots the initial hiccups ( desktop fragmenting and shut down applet) seem to have sorted themselves out. Amazing stuff for a beta 1 release. I love it.

---

### Post by king.pest on 2010-03-29
Ok, thanks, guess I will try to upgrade:)

---

### Post by seattle vic on 2010-03-29
I upgraded (update-manager -d) about a week ago and it went fine.  I like the new look, but was horrified that the min/max/close buttons moved to the left (what were they thinking?  Does Mac do it that way?), but nice that gconf-editor easily moves them back.

Speed seems as fast to the internet and it's been mostly stable with a few kernel crashes that don't seem to affect much.

The only problem I had was I think when it upgraded to 2.6.32.17 and during the restart it booted to the maintenance shell.  After 2 days of researching and trying things, re-installing gnome-session did the trick.  The upside to that is that I learned to connect wireless from the shell (need to disable network-manager).

So far it seems to be a winner, though I'm amazed how many packages are updated every day.  Nature of development I guess.

---

### Post by ImpressMe on 2010-03-31
First impression of LiveCD is that I am not going to install it, if every theme I choose has the buttons on the left. What a disappointment. Who the heck got that idea?

---

### Post by 98cwitr on 2010-03-31
> **switch10 said:**
> I don't like that the close, minimize, maximize buttons have moved.  It would take a while to get used to that.  The themes look good other than that.  



you can change that you know. Still liked 9.10 better...my splash screen looks 1998ish

---

### Post by Scott82 on 2010-03-31
> **98cwitr said:**
> you can change that you know. Still liked 9.10 better...my splash screen looks 1998ish

the splash screen for 9.10 beta did also if i remember right..... i'm sure it'll be all fancified and shmexy once it's the final release :D

---

### Post by ImpressMe on 2010-03-31
> **98cwitr said:**
> you can change that you know. Still liked 9.10 better...my splash screen looks 1998ish

How? On beta 1 (not install, using livecd) I can change theme, but the buttons are always on the left side, fx on Clearlooks.

EDIT: Solved: [http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/#comment-88812](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/#comment-88812)

---

### Post by razy60 on 2010-04-06
only real gripe i have is the same as in 9.10 in that ext4 format is rubbish when transferring large files to another HDD or usb device, the first 3/400 MB are fine then it takes forever for the rest then the manager just sits on the screen doing nothing for ages.

Raz

---

### Post by HolidayQueen on 2010-04-07
- I find having two tray's to be very confusing and somewhat pointless.

- on one of my computers i had to install fglrx to get fullscreen playback in VLC working properly. I don't know if this is a bug maybe the installer should have done this for me rather than leave me guessing.

- I wasn't too hot about the buttons on the left but i got used to it (i guess you gotta keep your interior decorators busy somehow...)

- ive also noticed this ugly white border around all my thumbnails. How do i remove?

- Very slow to automount my usb thumbdrive. what gives? (though i'll give you this: my tower is finally transferring at higher rates, 4-5mbps versus <= 1mbps before).

Things i did after installing: installed chromium, emesene, vlc, deluge, removed their default installation counterparts. removed Memenu.

Otherwise im very satisfied. Everything else pretty much worked out of the box and i can't remember the last time i upgraded/installed with so little fixing/tweaking afterwards.

---

### Post by Jordanwb on 2010-04-07
At first (alpha 1) it was fantastic; Fast boot times around 30 seconds, now it's passing 50 seconds (what is this? jaunty was faster); plymouth was optional, now it's depended on by almost everything; mtpfs is broken, no one seems to care; pidgin is horribly unstable; purple wallpaper; gnome-do doesn't start up half the time. I'm a sad lynx.

Anyone know how to disable plymouth completely?

[Edit]I got boot time down to 38 seconds. Which is good.

---

### Post by HolidayQueen on 2010-04-07
> **Jordanwb said:**
> At first (alpha 1) it was fantastic; Fast boot times around 30 seconds, now it's passing 50 seconds (what is this? jaunty was faster); plymouth was optional, now it's depended on by almost everything; mtpfs is broken, no one seems to care; pidgin is horribly unstable; purple wallpaper; gnome-do doesn't start up half the time. I'm a sad lynx.

Anyone know how to disable plymouth completely?

[Edit]I got boot time down to 38 seconds. Which is good.

Odd, i thought plymouth was rather good. Before lucid, during the boot up process my screen would turn off and the booting would halt there. Which happenned about once in every 3 or 4 bootups. If you press escape during the splash you should be able to see what's going on underneath, maybe something else is holding up your boot process.

---

### Post by Jordanwb on 2010-04-08
> **HolidayQueen said:**
> Odd, i thought plymouth was rather good.

Never said it wasn't; although I think it's ugly. I'm thinking of making a fake plymouth and plymouth-theme-ubuntu-logo package and reinstall. That way the real plymouth isn't installed but the dependencies are satisfied.

> **HolidayQueen said:**
> maybe something else is holding up your boot process.

My CPU is maxed out for most of the booting, the CPU is the bottleneck.

---

### Post by GoldNugget on 2010-04-09
I've been running Lucid for a few weeks on my eeepc 900 20G. It is remarkably stable and all hardware works OTB. I still get an error on boot notifying me that my battery may be broken but the battery monitor in the panel works fine. I seem to be getting slightly better time out of the battery.

Installing Blueman from the repositories allowed me to easily tether my Verizon Blackberry to use as a wireless modem. (I use an inexpensive usb adapter).

Docky sometimes crashes quietly and will occasionally warn me that composting must be enabled (it is enabled and working fine.)

I moved the buttons back to the right side in the order I am accustomed. It wasn't difficult for me, but I think it should be an option in the Appearances options for newcomers.

Other than a few small annoyances I am liking Lucid. I could live without the purple wallpaper but overall the new look is much better. The music store is nice and the Software Center has a nice polish. Lucid has a stable feel and I think it will make a good LTS version. 

Thanks Ubuntu and Debian developers. We love you.

---

### Post by LiquidMeson on 2010-04-09
The new red folder icons are too strong. Its like a bad cocktail. Its distracting, and almost disturbing. Especially against a soft background or green wallpaper. Imo.

I was trying to think of analogy for a couple that are trying to "over power each other", referring to purple and orange,  and someone replied, "gay-sex". lol. So idk, maybe this is a good thing.

---

