---
title: "Great Upgrade from Ubuntu 16.04 to 18.04 but watch out for Baloo"
date: 2021-03-12
forum: Installation &amp; Upgrades
---

### Post by atrab101 on 2021-03-12
I had been concerned about possible Unity issues, as well as a slower system from various forum comments I had seen on upgrading to 18.04.  I like to explore new things very slowly, and my 16.04 system had been working perfectly for years, since I painlessly upgraded from 14.04.  I have been 5 years with Ubuntu on my dual-boot system with Windows XP (for lots of old stuff but no Internet access now).  

I followed recommendations about updating apps before the upgrade and had only installed applications from the Ubuntu repositories.  In Software and Updates I selected to notify me of new LTS versions, and the process started.  The instructions were easy to follow and what a smooth process resulted!  It took less than an hour for everything.

My wife would not easily tolerate a desktop environment change and I like Unity, so I was glad to see the easy option to log in with and retain Unity.  Everything looked almost exactly the same.  My programs were supported and updated.  Everything worked perfectly, including printer and scanner.  I am glad that Gnome is still a login option that I can explore in the future.

My system has ASUS M5A97 R2.0 Motherboard, AMD FX8300 processor , 8GB Kingston HyperX PC1600 and Samsung EVO850 500GB SSD.  This was more than enough for 18.04.  But I soon noticed that the system seemed more sluggish than 16.04 at times.  It also took 30 seconds to shut down instead of 2 seconds.  I looked in KSysGuard and saw that "Baloo" was consuming about 4GB of memory, really taking all available to within about 250MB of the 8GB total.  So my available memory was hovering at about 250MB, whereas I typically had 5GB available in 16.04.  After some searching, I found that there were many comments on Baloo and the desire to get rid of it.  I found that some had various schemes for completely uninstalling it, others just disabled baloo_file_extractor.  I found that the disable was easy with the command: balooctl disable.  Rebooted and baloo has not come back in three weeks.  System is at least as fast (video better benchmark) than 16.04.  The system is never sluggish and shuts down in 2 seconds again.  Available memory is typically 4GB.  

I am amazed at how trouble-free this upgrade was.  Hats off to Ubuntu developers that even allowed me to retain Unity until I have a chance to explore Gnome.  

I have two areas to ask about: 
1) Why is baloo included in 18.04, and is it something that most users want?  Apparently it is enabled by default, and could it be the reason that in the past I saw many comments about slowed down systems in 18.04?  Am I likely to run into any problems because I disabled it?  I personally have never used such a program.  
2) There obviously must be advantages with Gnome that I am sure I will explore in the future.  Can I just alternate with Unity on a per login basis, without creating any problems with my system (Gnome affecting Unity or other way around)?

Again, many thanks to the developers and those who support this informative forum.  I have had a really great Ubuntu journey these last 5 years.  My use of my computer repair skills is now limited to fixing my daughter's Windows 10 computer problems.  :D

---

### Post by DuckHook on 2021-03-13
I'm positive the devs would appreciate your sentiments, but this is almost entirely a user supported forum and the devs rarely if ever visit here. They do hang around their own IRC channel, discourse and Launchpad of course, but the latter is strictly for technical/ppa type activities.

Glad you found the upgrade painless, but what are you doing with baloo in the first place? It is not part of a default vanilla Ubuntu install. Did you have Kubuntu or KDE running at some point? Did you install Kubuntu apps?

It is not a good idea to mix DEs. Your experience with baloo is very much a case in point. Strange stuff starts to happen and you end up playing whack&#8209;a&#8209;mole with your OS. My overriding motto is KISS, especially when it comes to the base OS.

If you tried KDE at some point, it is almost impossible to remove its files now. They will be scattered all over your install in several thousand pieces. I note that you also have KSysGuard. This is an indication of either past KDE install or of Kubuntu apps/components so massive that they drag in dozens if not hundreds of dependencies. In my opinion, this is an aspect of the Software Centre that is inadequately explained. Apps are dressed up all nice and pretty, but the underlying dependencies and context are completely hidden.

Perhaps a very (and I mean *very*) short primer is in order. Apologies if you already know this stuff:

Because Ubuntu comes in so many flavours, it mashes apps together in the Software Centre rather indiscriminately. However, there are still big consequences to installing apps meant for one flavour into another. The biggest drawback is that they drag in a lot of dependencies that are not "native" to the flavour you are running. This bloats your install up with strange libraries, monkeys with your config files, makes everything more complicated (and therefore brittle) and increase everything from risk of breakage to attack surface to problems with upgrades.

This is why my first recommendation to all general users is to keep their basic install as absolutely close to default as possible. I run many apps inside containers or VMs. Utilities are kept to a minimum. PPAs are verboten except absolutely proven ones like VirtualBox. Even snaps are the absolute minimum—mainly LXD for containerization.

When considering apps, do lots of research first. Watch out for the different flavours. Kubuntu stuff often (but not always) start with "k"—hence, KSysGuard. I will always install from the command line, never the Software Centre. It doesn't give me the control or the feedback that I want. By using apt, I can easily do: ```
sudo apt install -s ksysguard
```…the use of the -s flag simulates an install which gives me the chance to see how many dependencies will be dragged in. If it's massive, I rethink my whole strategy.

Re: Gnome

Canonical has decided, for better or worse, that Unity is not part of its future. To be sure, there is a dedicated following of Unity fans who are trying hard to make Unity remix an official flavour. If that comes to pass, then "Unibuntu" (I'm making this up as I go) could become a viable alternative. Until it does, you are living on borrowed time and will need to make the jump to Gnome sooner or later. I have no dog in this fight. I used Unity for years and loved it. I now use Gnome and love it. I have XFCE (Xubuntu) installed on my leaner machines and the really underpowered have Lubuntu (LXQT). I frankly do not understand why people go on jihads about their DE and find that I can use anything with equal happiness.

Please have a look at the link in my sig: The Best 'buntu Flavour. It will clarify a lot of your questions and provide context to the foregoing.

My overriding piece of advice remains: ***don't mix DEs***. If you want to try out Gnome (vanilla Ubuntu), spin up a VM, install it and play with it to your heart's content. Same goes for any of the other flavours. But keep your base install squeaky clean and as close to default as humanly possible. Should you decide that the time is right to move to Gnome, then do a virgin install and then keep it that way. You will pat yourself on the back for doing this when all of your future upgrades go painlessly and you don't end up with services like baloo unexpectedly poking their heads up and raspberrying you.

---

### Post by grahammechanical on 2021-03-13
May I make a point for the future? Ubuntu 20.04 does not have Unity 7 in its repositories. When I upgraded from 18.04 (which I could login to with Unity 7 or Gnome 3 shell) to 20.04 I was asked if I wanted the removal of obsolete packages. I agreed and Unity 7 was removed. There you go. And yes you can login to either Unity or Gnome shell on a log in basis. We do not have to reboot. Just log out and then select the desktop before loging back in

Regards

---

### Post by DuckHook on 2021-03-13
> **grahammechanical said:**
> …you can login to either Unity or Gnome shell on a log in basis. We do not have to reboot. Just log out and then select the desktop before loging back in…
There you go. Had totally forgotten that Bionic had both DEs side&#8209;by&#8209;side. Just two short years ago. Brain like a sieve these days. :(

---

### Post by atrab101 on 2021-03-13
> **DuckHook said:**
> 
If you tried KDE at some point, it is almost impossible to remove its files now. They will be scattered all over your install in several thousand pieces. I note that you also have KSysGuard. This is an indication of either past KDE install or of Kubuntu apps/components so massive that they drag in dozens if not hundreds of dependencies. In my opinion, this is an aspect of the Software Centre that is inadequately explained. Apps are dressed up all nice and pretty, but the underlying dependencies and context are completely hidden.

Perhaps a very (and I mean *very*) short primer is in order. Apologies if you already know this stuff:

Because Ubuntu comes in so many flavours, it mashes apps together in the Software Centre rather indiscriminately. However, there are still big consequences to installing apps meant for one flavour into another. The biggest drawback is that they drag in a lot of dependencies that are not "native" to the flavour you are running. This bloats your install up with strange libraries, monkeys with your config files, makes everything more complicated (and therefore brittle) and increase everything from risk of breakage to attack surface to problems with upgrades.

This is why my first recommendation to all general users is to keep their basic install as absolutely close to default as possible. I run many apps inside containers or VMs. Utilities are kept to a minimum. PPAs are verboten except absolutely proven ones like VirtualBox. Even snaps are the absolute minimum—mainly LXD for containerization.



Thanks for your very informative reply.  Never tried KDE.  I have used only Unity since installing 14.04 over 5 years ago.  Two easy system upgrades after that.  Probably about 2 weeks after my initial 14.04 installation, I installed KSysGuard because I like to see what is going on "under the hood."  Other "K" programs I nave installed are K4DirStat, Kdenlive and KDE Partition Manager.  I see there is also a browser, Konqueror, that I think just came along with 18.04.  Anyway, I am sure I only installed from Ubuntu repositories and the Ubuntu provided software center.  I do have Synaptic Package Manager installed which shows that I have 2749 installed, 0 broken, 0 to install/upgrade, 0 to remove.  

I definitely don't "know all this stuff" and am glad to have the info you have provided.  I read the info at the bottom of your post as you suggested.  Out of blissful ignorance, I never looked at a PPA, and it seems that is a very good thing!  

So I really do think my actions have kept things pretty close to default and there remains the mystery...where did Baloo come from?  Never appeared until I did the 18.04 upgrade, and I made no changes whatsoever before noticing it.  I guess it is good that I had KSysGuard to examine what was going on in my system.  Is there another program without KDE heritage that is available in Ubuntu to provide the same info?

Since my system is really running great now, I decided not to try to uninstall Baloo but just stick with it disabled.  Do you agree that this is a good approach?

Thanks again for all the information you provided.  I might have been getting over-confident that Ubuntu is bullet proof.  I will approach software installations and system upgrades with plenty of caution now.  I do think that Ubuntu is almost bullet proof when compared with my Windows experience over the years.  In 5 years with Ubuntu, I have never had a "BSOD" type experience that required a hard reset.  I have received the message "an unexpected error has occured," perhaps 10 times in 5 years, but I just submitted a report and continued my work without further problem or need to reboot.  I love Ubuntu.  :D

---

### Post by DuckHook on 2021-03-13
Ah. Okay. The "k" apps that you installed were indeed Kubuntu apps.

Another short primer then:

KDE uses Qt libraries whereas Gnome uses GTK. They are not incompatible so much as they are redundant. Redundancy bloats up your system as well as introduces more areas where conflicts can arise. Because you install from the Software Centre, all of the nitty gritty is hidden from you (another reason I don't like installing using GUI tools: I like to know exactly what's going on). My system is clean of Qt apps. This is what a CLI installation of your apps on my system shows:
```
duckhook@Zeus:~$  apt install -s ksysguard
NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  kio kpackagelauncherqml kpackagetool5 ksysguard-data ksysguardd kwayland-data kwayland-integration
  libdbusmenu-qt5-2 libfam0 libhfstospell10 libkf5archive5 libkf5attica5 libkf5auth-data libkf5authcore5
  libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5completion5 libkf5config-bin libkf5config-data
  libkf5configcore5 libkf5configgui5 libkf5configwidgets-data libkf5configwidgets5 libkf5coreaddons-data
  libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5
  libkf5declarative-data libkf5declarative5 libkf5doctools5 libkf5globalaccel-bin libkf5globalaccel-data
  libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin
  libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data libkf5itemviews5
  libkf5jobwidgets-data libkf5jobwidgets5 libkf5kiocore5 libkf5kiontlm5 libkf5kiowidgets5 libkf5kirigami2-5
  libkf5newstuff-data libkf5newstuff5 libkf5newstuffcore5 libkf5notifications-data libkf5notifications5
  libkf5package-data libkf5package5 libkf5quickaddons5 libkf5service-bin libkf5service-data libkf5service5
  libkf5solid5 libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5sysguard-bin
  libkf5sysguard-data libkf5textwidgets-data libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5
  libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5
  libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libksgrd7 libksignalplotter7 libkwalletbackend5-5
  libpolkit-qt5-1-1 libprocesscore7 libprocessui7 libqt5positioning5 libqt5qml5 libqt5quick5
  libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5texttospeech5 libqt5waylandclient5
  libqt5waylandcompositor5 libqt5webchannel5 libqt5webengine-data libqt5webenginecore5 libqt5webenginewidgets5
  libvoikko1 qml-module-org-kde-kirigami2 qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff
  qml-module-qtgraphicaleffects qml-module-qtqml-models2 qml-module-qtquick-controls2
  qml-module-qtquick-templates2 qml-module-qtquick-window2 qml-module-qtquick2 qtwayland5 sonnet-plugins
Suggested packages:
  fam qt5-qmltooling-plugins voikko-fi hspell
The following NEW packages will be installed:
  kio kpackagelauncherqml kpackagetool5 ksysguard ksysguard-data ksysguardd kwayland-data kwayland-integration
  libdbusmenu-qt5-2 libfam0 libhfstospell10 libkf5archive5 libkf5attica5 libkf5auth-data libkf5authcore5
  libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5completion5 libkf5config-bin libkf5config-data
  libkf5configcore5 libkf5configgui5 libkf5configwidgets-data libkf5configwidgets5 libkf5coreaddons-data
  libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5
  libkf5declarative-data libkf5declarative5 libkf5doctools5 libkf5globalaccel-bin libkf5globalaccel-data
  libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin
  libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data libkf5itemviews5
  libkf5jobwidgets-data libkf5jobwidgets5 libkf5kiocore5 libkf5kiontlm5 libkf5kiowidgets5 libkf5kirigami2-5
  libkf5newstuff-data libkf5newstuff5 libkf5newstuffcore5 libkf5notifications-data libkf5notifications5
  libkf5package-data libkf5package5 libkf5quickaddons5 libkf5service-bin libkf5service-data libkf5service5
  libkf5solid5 libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5sysguard-bin
  libkf5sysguard-data libkf5textwidgets-data libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5
  libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5
  libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libksgrd7 libksignalplotter7 libkwalletbackend5-5
  libpolkit-qt5-1-1 libprocesscore7 libprocessui7 libqt5positioning5 libqt5qml5 libqt5quick5
  libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5texttospeech5 libqt5waylandclient5
  libqt5waylandcompositor5 libqt5webchannel5 libqt5webengine-data libqt5webenginecore5 libqt5webenginewidgets5
  libvoikko1 qml-module-org-kde-kirigami2 qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff
  qml-module-qtgraphicaleffects qml-module-qtqml-models2 qml-module-qtquick-controls2
  qml-module-qtquick-templates2 qml-module-qtquick-window2 qml-module-qtquick2 qtwayland5 sonnet-plugins
0 upgraded, 115 newly installed, 0 to remove and 0 not upgraded.

```
115 dependencies for this one utility alone! So that's an example of what occurs when you install Qt apps onto a clean GTK environment.

I'm afraid that your current install is nothing close to default.

Here are the 79 dependencies for k4dirstat:
```
duckhook@Zeus:~$  apt install -s k4dirstat
NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  kio kwayland-data kwayland-integration libdbusmenu-qt5-2 libfam0 libhfstospell10 libkf5archive5 libkf5attica5
  libkf5auth-data libkf5authcore5 libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5completion5
  libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5 libkf5configwidgets-data
  libkf5configwidgets5 libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin
  libkf5dbusaddons-data libkf5dbusaddons5 libkf5doctools5 libkf5globalaccel-bin libkf5globalaccel-data
  libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin
  libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data libkf5itemviews5
  libkf5jobwidgets-data libkf5jobwidgets5 libkf5kiocore5 libkf5kiontlm5 libkf5kiowidgets5
  libkf5notifications-data libkf5notifications5 libkf5service-bin libkf5service-data libkf5service5 libkf5solid5
  libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5textwidgets-data
  libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5 libkf5waylandclient5
  libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin
  libkf5xmlgui-data libkf5xmlgui5 libkwalletbackend5-5 libpolkit-qt5-1-1 libqt5qml5 libqt5quick5
  libqt5texttospeech5 libqt5waylandclient5 libqt5waylandcompositor5 libvoikko1 qtwayland5 sonnet-plugins
Suggested packages:
  fam qt5-qmltooling-plugins voikko-fi hspell
The following NEW packages will be installed:
  k4dirstat kio kwayland-data kwayland-integration libdbusmenu-qt5-2 libfam0 libhfstospell10 libkf5archive5
  libkf5attica5 libkf5auth-data libkf5authcore5 libkf5codecs-data libkf5codecs5 libkf5completion-data
  libkf5completion5 libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5
  libkf5configwidgets-data libkf5configwidgets5 libkf5coreaddons-data libkf5coreaddons5 libkf5crash5
  libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5 libkf5doctools5 libkf5globalaccel-bin
  libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n-data
  libkf5i18n5 libkf5iconthemes-bin libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data
  libkf5itemviews5 libkf5jobwidgets-data libkf5jobwidgets5 libkf5kiocore5 libkf5kiontlm5 libkf5kiowidgets5
  libkf5notifications-data libkf5notifications5 libkf5service-bin libkf5service-data libkf5service5 libkf5solid5
  libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5textwidgets-data
  libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5 libkf5waylandclient5
  libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin
  libkf5xmlgui-data libkf5xmlgui5 libkwalletbackend5-5 libpolkit-qt5-1-1 libqt5qml5 libqt5quick5
  libqt5texttospeech5 libqt5waylandclient5 libqt5waylandcompositor5 libvoikko1 qtwayland5 sonnet-plugins
0 upgraded, 79 newly installed, 0 to remove and 0 not upgraded.
```
KDE Partition Manager, 82 dependencies:
```
duckhook@Zeus:~$  apt install -s partitionmanager
NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  kio kwayland-data kwayland-integration libdbusmenu-qt5-2 libfam0 libhfstospell10 libkf5archive5 libkf5attica5
  libkf5auth-data libkf5authcore5 libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5completion5
  libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5 libkf5configwidgets-data
  libkf5configwidgets5 libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin
  libkf5dbusaddons-data libkf5dbusaddons5 libkf5doctools5 libkf5globalaccel-bin libkf5globalaccel-data
  libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin
  libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data libkf5itemviews5
  libkf5jobwidgets-data libkf5jobwidgets5 libkf5kiocore5 libkf5kiontlm5 libkf5kiowidgets5
  libkf5notifications-data libkf5notifications5 libkf5service-bin libkf5service-data libkf5service5 libkf5solid5
  libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5textwidgets-data
  libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5 libkf5waylandclient5
  libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin
  libkf5xmlgui-data libkf5xmlgui5 libkpmcore9 libkwalletbackend5-5 libpolkit-qt5-1-1 libqca-qt5-2
  libqca-qt5-2-plugins libqt5qml5 libqt5quick5 libqt5texttospeech5 libqt5waylandclient5 libqt5waylandcompositor5
  libvoikko1 qtwayland5 sonnet-plugins
Suggested packages:
  fam qt5-qmltooling-plugins voikko-fi btrfs-progs hfsplus hfsutils jfsutils reiser4progs reiserfsprogs xfsprogs
  hspell
The following NEW packages will be installed:
  kio kwayland-data kwayland-integration libdbusmenu-qt5-2 libfam0 libhfstospell10 libkf5archive5 libkf5attica5
  libkf5auth-data libkf5authcore5 libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5completion5
  libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5 libkf5configwidgets-data
  libkf5configwidgets5 libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin
  libkf5dbusaddons-data libkf5dbusaddons5 libkf5doctools5 libkf5globalaccel-bin libkf5globalaccel-data
  libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin
  libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data libkf5itemviews5
  libkf5jobwidgets-data libkf5jobwidgets5 libkf5kiocore5 libkf5kiontlm5 libkf5kiowidgets5
  libkf5notifications-data libkf5notifications5 libkf5service-bin libkf5service-data libkf5service5 libkf5solid5
  libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5textwidgets-data
  libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5 libkf5waylandclient5
  libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin
  libkf5xmlgui-data libkf5xmlgui5 libkpmcore9 libkwalletbackend5-5 libpolkit-qt5-1-1 libqca-qt5-2
  libqca-qt5-2-plugins libqt5qml5 libqt5quick5 libqt5texttospeech5 libqt5waylandclient5 libqt5waylandcompositor5
  libvoikko1 partitionmanager qtwayland5 sonnet-plugins

```
And the granddaddy of them all, KDenLive with 202:
```
duckhook@Zeus:~$  apt install -s kdenlive
NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  breeze-icon-theme catdoc dvgrab frei0r-plugins kaccounts-providers kactivities-bin kactivitymanagerd
  kde-cli-tools kde-cli-tools-data kdeconnect kded5 kdenlive-data keditbookmarks kinit kio kpackagelauncherqml
  kpackagetool5 kpeople-vcard kwayland-data kwayland-integration libaccounts-glib0 libaccounts-qt5-1
  libdbusmenu-qt5-2 libebur128-1 libepub0 libfakekey0 libfam0 libgavl1 libhfstospell10 libkaccounts1
  libkf5activities5 libkf5archive5 libkf5attica5 libkf5auth-data libkf5auth5 libkf5authcore5 libkf5bluezqt-data
  libkf5bluezqt6 libkf5bookmarks-data libkf5bookmarks5 libkf5calendarevents5 libkf5codecs-data libkf5codecs5
  libkf5completion-data libkf5completion5 libkf5config-bin libkf5config-data libkf5configcore5 libkf5configgui5
  libkf5configwidgets-data libkf5configwidgets5 libkf5contacts-data libkf5contacts5 libkf5coreaddons-data
  libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5dbusaddons5
  libkf5declarative-data libkf5declarative5 libkf5doctools5 libkf5filemetadata-bin libkf5filemetadata-data
  libkf5filemetadata3 libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5
  libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin libkf5iconthemes-data libkf5iconthemes5
  libkf5idletime5 libkf5itemviews-data libkf5itemviews5 libkf5jobwidgets-data libkf5jobwidgets5
  libkf5kcmutils-data libkf5kcmutils5 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiogui5 libkf5kiontlm5
  libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff-data libkf5newstuff5 libkf5newstuffcore5
  libkf5notifications-data libkf5notifications5 libkf5notifyconfig-data libkf5notifyconfig5 libkf5package-data
  libkf5package5 libkf5parts-data libkf5parts-plugins libkf5parts5 libkf5people-data libkf5people5
  libkf5peoplebackend5 libkf5peoplewidgets5 libkf5plasma5 libkf5plasmaquick5 libkf5pty-data libkf5pty5
  libkf5pulseaudioqt2 libkf5purpose-bin libkf5purpose5 libkf5quickaddons5 libkf5service-bin libkf5service-data
  libkf5service5 libkf5solid5 libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5su-bin
  libkf5su-data libkf5su5 libkf5textwidgets-data libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data
  libkf5wallet5 libkf5waylandclient5 libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data
  libkf5windowsystem5 libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libkwalletbackend5-5 libkworkspace5-5
  libmlt++3 libmlt-data libmlt6 libmovit8 libphonon4qt5-4 libphonon4qt5-data libpolkit-qt5-1-1 libpoppler-qt5-1
  libqca-qt5-2 libqca-qt5-2-plugins libqt5positioning5 libqt5qml5 libqt5quick5 libqt5quickcontrols2-5
  libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5sensors5 libqt5texttospeech5 libqt5waylandclient5
  libqt5waylandcompositor5 libqt5webchannel5 libqt5webkit5 libquicktime2 librtaudio6 librttr-core0.9.6
  libsignon-plugins-common1 libsignon-qt5-1 libsox-fmt-alsa libsox-fmt-base libsox3 libvoikko1 libxcb-composite0
  libxcb-damage0 libzip5 melt oxygen-icon-theme phonon4qt5 phonon4qt5-backend-vlc plasma-framework
  qml-module-org-kde-bluezqt qml-module-org-kde-kconfig qml-module-org-kde-kirigami2
  qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff
  qml-module-org-kde-people qml-module-org-kde-purpose qml-module-qtgraphicaleffects qml-module-qtqml-models2
  qml-module-qtquick-controls qml-module-qtquick-controls2 qml-module-qtquick-dialogs qml-module-qtquick-layouts
  qml-module-qtquick-privatewidgets qml-module-qtquick-templates2 qml-module-qtquick-window2 qml-module-qtquick2
  qml-module-ubuntu-onlineaccounts qtwayland5 recordmydesktop signon-plugin-oauth2 sonnet-plugins swh-plugins
Suggested packages:
  python-nautilus khelpcenter fam kde-telepathy-send-file qt5-qmltooling-plugins libsox-fmt-all voikko-fi
  phonon4qt5-backend-gstreamer hspell
The following NEW packages will be installed:
  breeze-icon-theme catdoc dvgrab frei0r-plugins kaccounts-providers kactivities-bin kactivitymanagerd
  kde-cli-tools kde-cli-tools-data kdeconnect kded5 kdenlive kdenlive-data keditbookmarks kinit kio
  kpackagelauncherqml kpackagetool5 kpeople-vcard kwayland-data kwayland-integration libaccounts-glib0
  libaccounts-qt5-1 libdbusmenu-qt5-2 libebur128-1 libepub0 libfakekey0 libfam0 libgavl1 libhfstospell10
  libkaccounts1 libkf5activities5 libkf5archive5 libkf5attica5 libkf5auth-data libkf5auth5 libkf5authcore5
  libkf5bluezqt-data libkf5bluezqt6 libkf5bookmarks-data libkf5bookmarks5 libkf5calendarevents5 libkf5codecs-data
  libkf5codecs5 libkf5completion-data libkf5completion5 libkf5config-bin libkf5config-data libkf5configcore5
  libkf5configgui5 libkf5configwidgets-data libkf5configwidgets5 libkf5contacts-data libkf5contacts5
  libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-bin libkf5dbusaddons-data
  libkf5dbusaddons5 libkf5declarative-data libkf5declarative5 libkf5doctools5 libkf5filemetadata-bin
  libkf5filemetadata-data libkf5filemetadata3 libkf5globalaccel-bin libkf5globalaccel-data libkf5globalaccel5
  libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-bin
  libkf5iconthemes-data libkf5iconthemes5 libkf5idletime5 libkf5itemviews-data libkf5itemviews5
  libkf5jobwidgets-data libkf5jobwidgets5 libkf5kcmutils-data libkf5kcmutils5 libkf5kiocore5
  libkf5kiofilewidgets5 libkf5kiogui5 libkf5kiontlm5 libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff-data
  libkf5newstuff5 libkf5newstuffcore5 libkf5notifications-data libkf5notifications5 libkf5notifyconfig-data
  libkf5notifyconfig5 libkf5package-data libkf5package5 libkf5parts-data libkf5parts-plugins libkf5parts5
  libkf5people-data libkf5people5 libkf5peoplebackend5 libkf5peoplewidgets5 libkf5plasma5 libkf5plasmaquick5
  libkf5pty-data libkf5pty5 libkf5pulseaudioqt2 libkf5purpose-bin libkf5purpose5 libkf5quickaddons5
  libkf5service-bin libkf5service-data libkf5service5 libkf5solid5 libkf5solid5-data libkf5sonnet5-data
  libkf5sonnetcore5 libkf5sonnetui5 libkf5su-bin libkf5su-data libkf5su5 libkf5textwidgets-data
  libkf5textwidgets5 libkf5wallet-bin libkf5wallet-data libkf5wallet5 libkf5waylandclient5
  libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin
  libkf5xmlgui-data libkf5xmlgui5 libkwalletbackend5-5 libkworkspace5-5 libmlt++3 libmlt-data libmlt6 libmovit8
  libphonon4qt5-4 libphonon4qt5-data libpolkit-qt5-1-1 libpoppler-qt5-1 libqca-qt5-2 libqca-qt5-2-plugins
  libqt5positioning5 libqt5qml5 libqt5quick5 libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5quickwidgets5
  libqt5sensors5 libqt5texttospeech5 libqt5waylandclient5 libqt5waylandcompositor5 libqt5webchannel5
  libqt5webkit5 libquicktime2 librtaudio6 librttr-core0.9.6 libsignon-plugins-common1 libsignon-qt5-1
  libsox-fmt-alsa libsox-fmt-base libsox3 libvoikko1 libxcb-composite0 libxcb-damage0 libzip5 melt
  oxygen-icon-theme phonon4qt5 phonon4qt5-backend-vlc plasma-framework qml-module-org-kde-bluezqt
  qml-module-org-kde-kconfig qml-module-org-kde-kirigami2 qml-module-org-kde-kquickcontrols
  qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-newstuff qml-module-org-kde-people
  qml-module-org-kde-purpose qml-module-qtgraphicaleffects qml-module-qtqml-models2 qml-module-qtquick-controls
  qml-module-qtquick-controls2 qml-module-qtquick-dialogs qml-module-qtquick-layouts
  qml-module-qtquick-privatewidgets qml-module-qtquick-templates2 qml-module-qtquick-window2 qml-module-qtquick2
  qml-module-ubuntu-onlineaccounts qtwayland5 recordmydesktop signon-plugin-oauth2 sonnet-plugins swh-plugins
0 upgraded, 202 newly installed, 0 to remove and 0 not upgraded.

```
One of these, or probably some other that you may not remember, dragged in baloo.

When I want to run an app like KDenLive (which is a great app BTW), I will spin up a container and run it inside. That way, I preserve my pristine default base install. *I am **NOT** recommending this for you.* Containers are not trivial. You can get a sense of what it entails by looking at the link in my sig: Sandboxing Apps with LXD

What you may find useful is an easier to implement technology: Virtual Machines. Lots of people find VirtualBox to be quite friendly. If you feel like taking on a bigger challenge, then KVM is native to Linux and built right into the kernel. A web search will give plenty of tutorials to implement either.

If your current install is working nicely, there is no reason to change anything. However, you should be aware that it is very far away from being default at this point. In the event that you go to Gnome, that would be the time to do a clean fresh install and not bring along these apps.

There are tools that can replace most of these. I will post some suggestions next.

---

### Post by DuckHook on 2021-03-13
[LIST]
[*]The native GTK partition manager is gparted: ```
sudo apt install gparted
```
[*]A better way to get similar functionality to ksysguard is to first install lm-sensors and hddtemp. Then configure them to work properly. In the case of hddtemp, you *may* want to run it as a daemon, though this adds another service. Then when all that has been properly done, install psensor to show all the statistics on the system tray: ```
sudo apt install lm-sensors hddtemp psensor
```
[*]The GTK equivalent of k4dirstat is baobab: ```
sudo apt install baobab
```
[*]KDenLive is a toughy. It's an excellent app and there's nothing quite like it on the GTK side. Flowblade has high reputation and enthusiastic supporters but apparently a steep learning curve. Blender is very popular but is more about 2D/3D animation. PiTiVi is lightweight and drags in very few dependencies but may not be feature rich enough for you. Video editors are very personal and it would be a shame to force yourself to change tools for the sake of a technically "cleaner" system. I would rather recommend that you install KDenLive onto a VM, then continue to use it happily.
[/LIST]
Here's a thought: you seem to be quite enamoured of KDE apps. Would you consider installing Kubuntu instead? I would suggest downloading it and running it as a LiveUSB for a test drive. Word to the wise though: if you decide that you would actually be happier in the Kubuntu/Qt universe, do not then go mixing GTK apps into your Kubuntu install, else you will be back to square one playing whack&#8209;a&#8209;mole again!

---

### Post by atrab101 on 2021-03-14
> **DuckHook said:**
> Ah. Okay. The "k" apps that you installed were indeed Kubuntu apps.

Another short primer then:

One of these, or probably some other that you may not remember, dragged in baloo.

When I want to run an app like KDenLive (which is a great app BTW), I will spin up a container and run it inside. That way, I preserve my pristine default base install. *I am **NOT** recommending this for you.* Containers are not trivial. You can get a sense of what it entails by looking at the link in my sig: Sandboxing Apps with LXD

What you may find useful is an easier to implement technology: Virtual Machines. Lots of people find VirtualBox to be quite friendly. If you feel like taking on a bigger challenge, then KVM is native to Linux and built right into the kernel. A web search will give plenty of tutorials to implement either.

If your current install is working nicely, there is no reason to change anything. However, you should be aware that it is very far away from being default at this point. In the event that you go to Gnome, that would be the time to do a clean fresh install and not bring along these apps.

There are tools that can replace most of these. I will post some suggestions next.

What a revelation to me.  As you say, not nearly a default system I have!  478 total dependencies for 4 Kubuntu apps, which I did not realize were Kubuntu.  So now I am aware of the potential pitfalls, and I will be more wary in  the future and do the trial view before installing programs.  There is no apparent need to investigate the origin of baloo on my system any longer.  I do wonder how many have it and don't realize that it is making their system sluggish.  I think I will not change anything now as you say, since everything works.  Doing a fresh install if I change to Gnome sounds like a very good idea.  For now the system boots in about 10 seconds and shuts down in 2.  All apps and Internet are very fast with no strain on resources.  Moving my system to a Samsung 850 EVO SSD from a Western Digital Black HDD about 3 years ago with a Clonezilla disk image made everything much faster than before.  That probably helps me avoid any visible effects of system bloat.  Virtual Machines sound like an interesting area to study for the future.  I will always have a fresh disk image available if I experiment; I routinely do them weekly and just before doing anything that appears risky.

---

### Post by atrab101 on 2021-03-14
> **DuckHook said:**
> 
Here's a thought: you seem to be quite enamoured of KDE apps. Would you consider installing Kubuntu instead? I would suggest downloading it and running it as a LiveUSB for a test drive. Word to the wise though: if you decide that you would actually be happier in the Kubuntu/Qt universe, do not then go mixing GTK apps into your Kubuntu install, else you will be back to square one playing whack&#8209;a&#8209;mole again!

Regarding the Gnome apps you describe, I already have gparted, psensor and baobab installed on my system.  I guess I installed the KDE apps for comparison long ago.  I do note that psensor with its associated apps does not appear to provide a detailed look at memory consumption by processes, which is something I like to be able to see and that is available in KSysGuard.

At this time I don't think I would consider installing Kubuntu because I am so familiar with my Ubuntu LTS system and it meets all my needs.  I think I have read that Kubuntu is a "lighter" distribution, so at some point in the future my very old system may create the need to make a change.  I do intend to keep my current system configuration for as long as possible because it is fully compatible with Windows XP, for my dual-boot arrangement.  When I built the system 5 years ago I selected the last generation of ASUS motherboards, as well as AMD processors and video cards that had XP compatibility, for that reason.  I also have spare parts if things break.  :)

---

### Post by atrab101 on 2021-03-14
> **grahammechanical said:**
> May I make a point for the future? Ubuntu 20.04 does not have Unity 7 in its repositories. When I upgraded from 18.04 (which I could login to with Unity 7 or Gnome 3 shell) to 20.04 I was asked if I wanted the removal of obsolete packages. I agreed and Unity 7 was removed. There you go. And yes you can login to either Unity or Gnome shell on a log in basis. We do not have to reboot. Just log out and then select the desktop before loging back in

Regards
Thanks for the info.  So I can easily try out the look and feel of the Gnome desktop.  I am really glad I was given this option.  Looks like I will be dragged from Unity when I install 20.04 within the next 2 years.  On the other hand, I have read in many posts that Unity users like Gnome when they get used to it.  I tend to stick with familiar computer things if I like them, but don't find it hard to make changes when I need to.  My wife really dislikes any changes in technology (especially computers), so I am concerned about her reaction to "goodby Unity."  Let's say we try Gnome for several days or weeks, through shutdowns and reboots, and she still doesn't like Gnome.  Is there still no problem changing back to Unity after days or weeks using Gnome exclusively?  Probably a stupid question, but I ask anyway.  I have learned that not fearing looking stupid has been of great benefit to me over my 72 years.  :oops:

---

### Post by CatKiller on 2021-03-14
> **atrab101 said:**
> There is no apparent need to investigate the origin of baloo on my system any longer.  I do wonder how many have it and don't realize that it is making their system sluggish.

What Baloo does is index all your files to create a database of contents and metadata so that it's quicker to search for things. Gnome comes with exactly the same thing, called Tracker. They're both intended to run in the background so that they don't bother you, but they both had bugs around the same time that caused them to impact the system performance. Later versions of both are better behaved. Windows' and OS X's file indexers have also had exactly the same problem; it's just an inherently tricky balance to hit.

Your problem wasn't inherently that you installed KDE applications, just that one of the ones you did had a bug. You could have experienced exactly the same thing even if you'd never installed anything. 

If you don't regularly search the contents of files there's no downside to disabling Baloo or Tracker.

---

### Post by atrab101 on 2021-03-14
> **CatKiller said:**
> 

Your problem wasn't inherently that you installed KDE applications, just that one of the ones you did had a bug. You could have experienced exactly the same thing even if you'd never installed anything. 

If you don't regularly search the contents of files there's no downside to disabling Baloo or Tracker.
I installed the few KDE applications about 5 years ago, after my initial Ubuntu 14.04 installation.   I have done 2 system upgrades since then, the latest to 18.04.   I presume that updates to these Kubuntu applications have occurred since the initial installation of them.    The curious thing is that I had never seen or heard of baloo until immediately after the 18.04 upgrade, when I investigated my slower system.    I also don't think baloo was running previously because I never noticed it in a review of running processes, and my system was always very fast with plenty of free memory.  So why would it appear suddenly with this upgrade (and running) with me having done nothing to invoke it.?

I see that baloo and tracker both are listed in the Synaptic Package Manager but are not listed under those names in the current Software Center provided with Ubuntu 18.04.  In Synaptic it of course shows baloo to be installed.   Tracker is not installed, so apparently it does not come with the default 18.04 installation.  I don't regularly search contents of files, so I will just stick with baloo disabled and do not plan to install tracker.  

Thanks for your explanation of baloo and its bug.   I am very satisfied with my system, but I still wonder how the upgrade to 18.04 could have triggered the baloo situation, by either installing it, turning it on, or both.  I do realize that this is a trivial issue for me now, but there may be users out there that have the same issue and remain unaware of what is causing it.  It did cause serious performance issues on my system until I disabled it.

---

### Post by CatKiller on 2021-03-14
> **atrab101 said:**
> I also don't think baloo was running previously because I never noticed it in a review of running processes, and my system was always very fast with plenty of free memory.

You wouldn't. When it's working as intended it uses essentially no CPU time, and a marginal increase in I/O when the system is otherwise idle. It's only that it wasn't working properly that caused you problems. It's been in the repositories since ~2014, I think. Before that KDE's file indexer was Nepomuk.

---

### Post by DuckHook on 2021-03-15
> **atrab101 said:**
> What a revelation to me.  As you say, not nearly a default system I have!  478 total dependencies for 4 Kubuntu apps, which I did not realize were Kubuntu.
Not quite 478 because some of those will have been duplicated across the 4 apps, but yeah, pretty ugly all the same.

I'm probably sounding like a broken record, but I find the Software Centre to be more a curse than a blessing. Though superficially "friendly", it duplicates the bad aspects of the proprietary app stores (better known as malware infested cesspools). It tells you nothing of technical importance and just pushes apps as eye candy—basically selling whiz&#8209;bang in lieu of substance or knowledge. Snap apps are mixed in with repo apps. Qt apps are jumbled with GTK. Well programmed models of efficiency are displayed side by side with dreadful unmaintained orphans. Just a dog's breakfast but with a pretty sugar coating slathered on top to hide the mess underneath. The reviews are also unfair and misleading: great apps get low ratings from newbies who haven't the faintest idea what they are doing; poor apps getting high ratings from others who are impressed with eye candy at the cost of, say, security.

FWIW, if you don't feel the need for any of those apps any more, it is a simple matter to remove them using apt. This will have the significant side benefit of removing their dependencies as well: ```
sudo apt purge <unwanted-pkg>
```

But be sure that you actually want to remove it. The command line won't coddle you. Once purged, all config files are also deleted. There's no going back and if you reinstall the app, you will have to set up all of your old customizations again.
> **atrab101 said:**
> …I do note that psensor with its associated apps does not appear to provide a detailed look at memory consumption by processes, which is something I like to be able to see and that is available in KSysGuard.
Then do what we power users do: fire up a Terminal session and simply type: ```
htop
```You will get all the memory usage info you want and feel like a professional geek while doing it.
> …I think I have read that Kubuntu is a "lighter" distribution
Kubuntu is one of the heaviest flavours. As heavy as Gnome. If you want lighter, go MATE or Lubuntu. I've mentioned the link in my sig before…
> …Windows XP, for my dual-boot arrangement.
Dual booting with XP <sigh>. Oh boy. OK. It's your neck, but in IT terms, if XP is not a dinosaur, then it is at least a Woolly Mammoth. It is dead. Extinct. Finito. More frighteningly, it is (and always was) a malware nightmare. Trouble in Technicolour with a capital 'T'. Do. Not. Use. It. If you have ancient apps that you simply *must* run on it, then jail the damn thing in one of those aforementioned VMs, disable the VM's NIC and run it fully sandboxed. That is the ***ONLY*** way to run XP safely today. If you have it hooked up to the Internet in any way, shape or form, you have opened yourself up to—oh… let's see—by now, several thousand exploits that millions of scumbags have perfected over the years to pwn unsuspecting guys like you.

Re Gnome: The Mrs will have another two-ish years before Bionic punches out, so there's still plenty of time. However, as already mentioned, sooner or later, she will have to make the jump. I was able to convince my better half to make the jump a few months ago through a combination of guilt tripping ("c'mon, *I'm* the one who has to maintain the damn thing!") to sheer bribery ("after our fine dinner out tonight, I'm going to upgrade your Ubuntu!").

---

### Post by atrab101 on 2021-03-16
> **DuckHook said:**
> 

I'm probably sounding like a broken record, but I find the Software Centre to be more a curse than a blessing.  ...The reviews are also unfair and misleading: great apps get low ratings from newbies who haven't the faintest idea what they are doing; poor apps getting high ratings from others who are impressed with eye candy at the cost of, say, security.

Then do what we power users do: fire up a Terminal session and simply type: ```
htop
```You will get all the memory usage info you want and feel like a professional geek while doing it.

Dual booting with XP <sigh>. Oh boy. OK. It's your neck, but in IT terms, if XP is not a dinosaur, then it is at least a Woolly Mammoth. It is dead. Extinct. Finito. More frighteningly, it is (and always was) a malware nightmare. Trouble in Technicolour with a capital 'T'. Do. Not. Use. It. If you have ancient apps that you simply *must* run on it, then jail the damn thing in one of those aforementioned VMs, disable the VM's NIC and run it fully sandboxed. That is the ***ONLY*** way to run XP safely today. If you have it hooked up to the Internet in any way, shape or form, you have opened yourself up to—oh… let's see—by now, several thousand exploits that millions of scumbags have perfected over the years to pwn unsuspecting guys like you.

Re Gnome: The Mrs will have another two-ish years before Bionic punches out, so there's still plenty of time. However, as already mentioned, sooner or later, she will have to make the jump. I was able to convince my better half to make the jump a few months ago through a combination of guilt tripping ("c'mon, *I'm* the one who has to maintain the damn thing!") to sheer bribery ("after our fine dinner out tonight, I'm going to upgrade your Ubuntu!").

Didn't have htop installed on my system, so I decided to install it.  Looked in Synaptic and saw the number of the repository version.  Then looked in Software Center and saw that it had this repository version as well as a snap version by different authors.  Both versions had exactly the same review info, highly favorable.  The snap version showed an eye candy picture, but the repository version had no picture available.  Snap version had a much larger installed program size.  Did the "-s" command to simulate installation and it showed a very simple installation, and it also showed the two different commands for snap and repository.  I entered the command for the non-snap version and installation was completed.  With command "htop" started program.  Very nice!  I had a fleeting feeling of being a geek but know that I really am very far from that.  At my age (72) it is unlikely I will ever even achieve half-geek.  :)  This confirmed your cautionary comments on the Software Center.  I personally like eye candy, and I have been more a GUI vs. command line person.  This leopard won't change his spots quickly but will at least be more aware.  Thank you for the tutorial comments.

Now for your comments on Windows XP.  I think you don't like!!  When my 15 year old XP computer died in late 2015.  I was faced with going to a newer version of Windows.  I had seen them all and didn't like them.  Plus I would have had to reinstall all my old stuff, if I could even find the programs.  I did have a current disk image of my XP system.  I restored the image to new hardware that I selected for both XP and Linux compatibility, utilizing my Acronis True Image program.  I realized that Internet with Windows XP was a short term prospect because all support would soon be dropped.  Soon thereafter I installed Ubuntu 14.04 on a separate drive in a dual-boot configuration.  I have quite a few programs in XP that I have used for many years that I still find useful.  Examples are financial analysis, photo negative/slide scanning, chess, as well as others.  I have a 2005 vintage Epson all-in-one where printing is dead, but the scanner still works very well and has fixtures to hold negatives and slides.  There are not Linux drivers for this scanner that provide the full range of functions.  New scanners with similar capabilities cost hundreds just for the scanner, so why not still use it for my current project of preserving memories? [B] 

I totally agree that Internet is no longer appropriate for XP[/B] so my NIC is disabled in Windows. It has no Internet connection.  As I see it, I have the best of both worlds.  Frozen Windows XP for some familiar and useful old stuff, plus the much better Ubuntu for the Internet and all things new. 

 XP was useful for the repair of my daughter's Windows 10 computer a few years ago.  The Spectre/Meltdown fiasco turned her computer into a brick with an automatic mandatory update of Windows 10 (as for millions of other AMD processor users).  Wouldn't boot or even do any analysis on the disk drive with anything provided by Windows 10.  Took her drive home, put it into my dual boot box and used a 2005 version of Norton Disk Doctor to repair it (hundreds of pages of errors).  Actually got her login screen to appear on my box.  Her computer was a little old, so I put her old drive in an external drive enclosure, and she then restored her data to a new computer that I picked out for her.  Couldn't convince her to go to Linux because she is a teacher and so much of that world is centered on Windows.  

This comment may make your skin crawl, but someone will probably have to pry Windows XP from my cold dead hands someday.  [-o<

I am glad to see that I am not the only one with a wife that doesn't like it when hubby makes changes to her technology.  You employed an excellent strategy.  I think I will do the same when the time is right.  

Best Regards

---

### Post by DuckHook on 2021-03-16
> **atrab101 said:**
> …This comment may make your skin crawl, but someone will probably have to pry Windows XP from my cold dead hands someday.  [-o<
…
I hope it won't shock you to learn that I still have XP too. But it is installed within a Virtual Machine and appropriately sandboxed with the virtual NIC disabled, so I'm okay. Like you, I still have a few ancient games and such that I run from time to time. Stuff like Sid Meier's Alpha Centauri won't run in WINE, and SMAC brings back so many fond memories that I just can't let it go. So "hate" would be too strong a word for my thoughts on XP. But I am aware of its thousands of holes. It's a horror show. However, if you have the NIC disabled, then you are unlikely to come to harm, so feel free to keep on truckin'.

Good Luck and Happy Ubuntuing!

---

### Post by rsteinmetz70112 on 2021-03-16
```
I am glad to see that I am not the only one with a wife that doesn't like it when hubby makes changes to her technology. You employed an excellent strategy. I think I will do the same when the time is right.
```

Every time someone makes the decision to change the GUI of any OS lots of users of every gender have heartburn and some will try to make the new version look just like the old one. I used to be like that, wondering why they decided to change the GUI that I was familiar with and liked. I suspect it is often devs or managers wanting something new without really improving usability. I once tried to make Linux look like XP and was pretty successful. I did it for the comfort of other users. I eventually decided that it was far easier to suck it up and go through a few weeks of disgruntled learning curve and keep everything more or less current.

---

