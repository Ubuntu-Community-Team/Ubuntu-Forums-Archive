---
title: "Ubuntu After Install - Recieving multiple crash reports"
date: 2015-04-24
forum: Installation &amp; Upgrades
---

### Post by apacheomega2 on 2015-04-24
Hello I'm new to Ubuntu (I switched over from Fedora) and I'm having trouble installing alot of packages. I have one crash report in particular saying sorry problem occured while installing software. Package: libcolord-gtk1:amd64 0.1.25-1.1build2. also there are other multiple problems when I try to install packages and repositories via command line it's always an error with the ppa.launchpad.net site

```
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main amd64 Packages                         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main i386 Packages                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main amd64 Packages                         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main i386 Packages                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main amd64 Packages                         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main i386 Packages                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main amd64 Packages                         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main i386 Packages                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main amd64 Packages                         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main i386 Packages                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en                         
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main amd64 Packages                         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main i386 Packages                          
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) vivid/main Translation-en                         
Fetched 26.0 MB in 52s (495 kB/s)                                              
Reading package lists... Done
W: Failed to fetch [http://ppa.launchpad.net/atareao/atareao/ubuntu/dists/vivid/InRelease](http://ppa.launchpad.net/atareao/atareao/ubuntu/dists/vivid/InRelease)  

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  

W: Failed to fetch [http://download.videolan.org/pub/debian/stable/InRelease](http://download.videolan.org/pub/debian/stable/InRelease)  

W: Failed to fetch [http://repo.mate-desktop.org/archive/1.8/ubuntu/dists/vivid/InRelease](http://repo.mate-desktop.org/archive/1.8/ubuntu/dists/vivid/InRelease)  

W: Failed to fetch [http://repo.steampowered.com/steam/dists/precise/InRelease](http://repo.steampowered.com/steam/dists/precise/InRelease)  

W: Failed to fetch [http://repo.steampowered.com/steam/dists/precise/Release.gpg](http://repo.steampowered.com/steam/dists/precise/Release.gpg)  Temporary failure resolving 'repo.steampowered.com'

W: Failed to fetch [http://repo.mate-desktop.org/archive/1.8/ubuntu/dists/vivid/main/binary-amd64/Packages](http://repo.mate-desktop.org/archive/1.8/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://repo.mate-desktop.org/archive/1.8/ubuntu/dists/vivid/main/binary-i386/Packages](http://repo.mate-desktop.org/archive/1.8/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-i386/Packages)  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise/steam amd64 Packages (/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_binary-amd64_Packages)
W: Duplicate sources.list entry [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise/steam i386 Packages (/var/lib/apt/lists/repo.steampowered.c
```


How do I fix this????

---

### Post by ian-weisser on 2015-04-24
404 Not Found: Try opening those URLs in a web browser.
The warning means those PPAs do not have packages for 15.04 (Vivid), so you should stop trying to use them.

W: Duplicate sources.list entry: Duplicate means just that - duplicate. It's listed more than once.

Open System Settings --> Software & Updates --> Other Software Tab. 
Uncheck (or delete) those 404 PPAs.
Uncheck (or delete) one of the duplicate repos.

---

### Post by apacheomega2 on 2015-04-24
@ian-weisser
Thanks for the reply I new I should have just stuck with the 14.10!!!
Should I just go back to that cause I really don't feel like tinkering around all the time - thats why I dropped Fedora 21.
You think there might be a place with the right ppa's because all the sites ay their methods work for 15.04 but they're al lying like a dog

---

### Post by Mark Phelps on 2015-04-24
In my own experience, it's generally a bad idea to go with a new release within only a few days of its release -- especially if you're going to use PPAs.

It's generally better to wait a few weeks, and watch the forums for problem posts on the new release, before installing it.

---

### Post by ian-weisser on 2015-04-24
> **apacheomega2 said:**
> Should I just go back to that cause I really don't feel like tinkering around all the time

If you don't want to tinker or reinstall, can you simply use the stable, tested, supported software in the Ubuntu repositories?
Is there a reason you need the PPAs?

---

### Post by apacheomega2 on 2015-04-25
@ian-weisser

 No really there&#8217;s not, I just thought they were the norm when using Ubuntu. With Fedora I never saw like PPAs there where just always a total lack of support.
So I don't need these PPA thingamajiggies then?

---

### Post by ian-weisser on 2015-04-25
> **apacheomega2 said:**
> So I don't need these PPA thingamajiggies then?

Correct. Supported Ubuntu software is not distributed from PPAs. Supported Ubuntu software is distributed from the Ubuntu repositories.

PPAs are ***personal*** repositories that *individuals* can use to distribute pretty much anything they want. Their original purpose was (and is) to make simple wide distribution for pre-release testing and experimentation. PPA software is supported only by the PPA author.

Instructions on the Ubuntu Wiki or AskUbuntu or UbuntuForums that guide you to a PPA should explain why the supported version in the Ubuntu repositories is not adequate.

---

### Post by apacheomega2 on 2015-04-25
Thanks

---

