---
title: "A Little Light Lubuntu Pruning"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by SteveDee on 2012-04-27
One of the reasons there are so many Linux distros (and flavours of 'Buntu) is that everyone has their own ideas on how an OS should look and what apps to use.

I use Lubuntu on a wide range of machines including desktops, thin clients and simple headless servers. One common theme is that the hardware is (just like me) old & feeble. So after completing the basic graphical install, I often remove some of the applications & services that I don't need.

I'm a great fan of graphical apps and generally use Synaptic to add/remove packages as it maintains a History of what I've done. However, I normally use the terminal for this initial pruning, using a saved list of unwanted applications.

I keep the command line details in a text file, that for Lubuntu 12.04 looks like this:-
```

#basic remove command
sudo apt-get remove 

#accessories: character map, calculator, disk burner & notes
gucharmap galculator xfburn xpad 

#games
ace-of-penguins 

#Graphics
mtpaint simple-scan libsane libsane-common

#internet
pidgin pidgin-libnotify pidgin-data sylpheed sylpheed-doc sylpheed-plugins sylpheed-i18n transmission transmission-gtk transmission-common chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg

#office
abiword abiword-common libabiword-2.9 gnumeric gnumeric-common osmo

#Sound & Video
audacious audacious-plugins audacious-plugins-data libaudclient2 libaudcore1 gnome-mplayer libgmlib0 libgmtk0 libgmtk0-data

#System Tools: Additional Drivers, Bluetooth, Software Centre & Update Notifier
jockey-gtk jockey-common blueman lubuntu-software-center update-notifier update-notifier-common

#All Together
sudo apt-get remove gucharmap galculator xfburn xpad ace-of-penguins mtpaint simple-scan libsane libsane-common pidgin pidgin-libnotify pidgin-data sylpheed sylpheed-doc sylpheed-plugins sylpheed-i18n transmission transmission-gtk transmission-common chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg abiword abiword-common libabiword-2.9 gnumeric gnumeric-common osmo audacious audacious-plugins audacious-plugins-data libaudclient2 libaudcore1 gnome-mplayer libgmlib0 libgmtk0 libgmtk0-data jockey-gtk jockey-common blueman lubuntu-software-center update-notifier update-notifier-common


```
So if I wanted to just remove Games, Graphics & Office apps, I'd copy from the file to the terminal the chucks of text to make up this string:-
```

sudo apt-get remove ace-of-penguins mtpaint simple-scan libsane libsane-common abiword abiword-common libabiword-2.9 gnumeric gnumeric-common osmo

```
The section "All Together" is the complete command to remove all apps I don't need. On 12.04 this seems to free up about 175MB of disk space.

I never seem to need Additional Drivers, Bluetooth or the automatic update feature. So I switch these off from Preferences > Desktop Sessions Settings, and (as you can see in the command string)remove Blueman, Jockey & update notifier software.

Of course you could start with a mini-install and build your system up from there. I have done this in the past, but I find the method above less of a drain on my time and a reasonable compromise.

---

### Post by marinara on 2012-04-27
i really don't get it.  It seems like you're just freeing up a few kilobytes on your hard disk.  Or am i wrong?

---

### Post by DrPCDr on 2012-04-28
Steve:

I deploy images of OS onto free space because I need only do things once.

I too like light and fast and have created an image of Linux Mint 9 LXDE that runs very quickly.

Someone is seeding it here:

[http://thepiratebay.se/torrent/7220650]("http://www.linkedin.com/redirect?url=http%3A%2F%2Fthepiratebay%2Ese%2Ftorrent%2F7220650&urlhash=ugdb&_t=tracking_disc")

I have uploaded it to my free dropbox account here:
[http://dl.dropbox.com/u/75743475/LM9LXDE_16F.tbi](http://dl.dropbox.com/u/75743475/LM9LXDE_16F.tbi)

[http://dl.dropbox.com/u/75743475/iflnet.iso](http://dl.dropbox.com/u/75743475/iflnet.iso)

[http://dl.dropbox.com/u/75743475/Read_Me.txt](http://dl.dropbox.com/u/75743475/Read_Me.txt)

[http://dl.dropbox.com/u/75743475/BOOTITNG.ISO](http://dl.dropbox.com/u/75743475/BOOTITNG.ISO)

Do try it out
[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

---

### Post by SteveDee on 2012-04-28
> **marinara said:**
> ...seems like you're just freeing up a few kilobytes on your hard disk...

...well MB rather than kB, but yeah, its just about removing apps that are not needed so they don't clutter up the menus or require pointless updating.

Lubuntu is the light member of the 'Buntu family, and personally I'd prefer a minimal download option with no apps, that just allowed me to boot into the desktop. From there I could then apply a single command line "recipe" to install my required apps in the form:-
```

sudo apt-get install audacious banshee camserv......

```

DrPCDr, from your pdf: "Where Linux is concerned, I am a baby just learning to crawl."
...I still haven't escaped from the womb!
If I can find some time during the next couple of weeks I'll take a closer look at this.

At work I currently deploy Linux images like this:-
 - configure linux on a test machine (add apps, create users & so on)
 - use Gparted to reduce partition size (this is to ensure I can deploy to any computer HDD size down to 20GB)
 - create image using Clonezilla

This image can then be deployed using Clonzilla, and takes around 2 minutes to write to disk. All that needs setting is the computer name.

---

### Post by marinara on 2012-04-29
there is a minimal version of lubuntu.  it's very minimal from what i hear

---

### Post by Cythes on 2012-05-17
I personally use Xubuntu, its quick and painless IMHO.

---

### Post by vasa1 on 2012-05-17
> **Cythes said:**
> I personally use Xubuntu, its quick and painless IMHO.
This thread is about Lubuntu and making it even lighter. It maybe a good idea to post about other flavors elsewhere.

---

### Post by daisyflower on 2012-05-18
There is no way the average user is going to know how "light" Lubuntu is compared to other installations of Ubuntu.  

I prefer Kubuntu on my desktop, but it was advised to use Xubuntu or  Lubuntu on my netbook.  After looking at screenshots, I chose Lubuntu.

I see a few minor changes, but again, I don't know how it is a better  choice than the Kubuntu netbook version,  [https://wiki.kubuntu.org/Kubuntu/Netbook](https://wiki.kubuntu.org/Kubuntu/Netbook)

For example, the notepad version of Kubuntu is called "Kate" and the  Lubuntu version is Leafpad.  Are we to assume Leafpad is smaller and  significantly better than Kate?

When using both, I don't notice any differences.

---

### Post by SteveDee on 2012-05-19
> **daisyflower said:**
> ...Are we to assume Leafpad is smaller and  significantly better than Kate?...

Think of the 'buntu versions as templates. Each contains variations to the basic file list, different Desktop environment, and a different choice of preinstalled applications.

I think the choice of 'buntu is more to do with general expectations. If you like desktop effects, and expect a lot of functionality to be built in, then start with Ubuntu.
If you have an old or low power computer, try a 'buntu that claims to be fast & light weight (e.g. Lubuntu, Xubuntu, & so on). Don't be put off because an app installed with the OS is not to your liking. Use Synaptic to install alternatives, and keep an eye on the size of dependencies which are included if you have space limitations.

The installed applications on 'buntu have the following implications:-
1. Hard drive space: not a problem in itself, if you have plenty of space.
2. Performance when running: consider your computer's capabilities
3. Drain on resources when not used: a few applications/services are loaded automatically.
4. Applications (& other software) that you never use: will be included in [pointless] updates, & may sit in your menu structure.

When it comes to application choice (like text editors), just choose those you prefer. Most of the time I use Leafpad, but I also use gEdit which has capabilities that I find useful. (I'd probably use Notepad++ if there was a Linux version!).

If you are trying different 'buntus, make a note of any performance factor that is important to you (e.g. boot time, app load time, cpu% usage when idle, & so on) to ensure a better comparison.

Having selected a 'buntu, you can then install the Apps you prefer, and remove the ones you don't need.

---

### Post by Xplorer4x4 on 2012-12-08
@SteveDee, thanks for the list. I will find this useful. Most of the package names are easy to figure out, but in a few cases, such as games, the package name is not so obvious.

---

