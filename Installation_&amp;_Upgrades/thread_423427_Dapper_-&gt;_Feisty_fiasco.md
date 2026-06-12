---
title: "Dapper -&gt; Feisty fiasco"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by illuminati11_13 on 2007-04-25
I've used Ubuntu for 7 months without needing help but now I've done something stupid.

I tried to upgrade from dapper to feisty in one go from the command line. (rather impulsively at that.)

This is what I did:

[I]sudo vi sources.list

:%s/dapper/feisty

sudo apt-get update

sudo apt-get  dist-upgrade

sudo apt-get -f install

sudo dpkg --configure -a[/I]

I rebooted the computer and the gdm won't start and I can't seem the start X (the command is startx right?, it's been a while) The Ubuntu loading screen is now in monochrome and I can't see the loading. My /home/*user* directory seems untouched fortunately and most of the programs I've install independently still seem to be there but there's no feasibly to verify all of them. 

Beyond this, I have absolutely no idea what's broken. What I want to know is what the easiest way to restore my system to a usable state. 

Bear in mind I've installed lots of third party software from source (mostly libraries and compilers).  I'd rather not loose these, but because most of my data is backed up on an external harddrive and I'm going to clone more /home/*user* directory, there's nothing I can't afford to just reinstall.

Thank you for any help.

---

### Post by zvacet on 2007-04-26
```
sudo dpkg-reconfigure xserver-xorg
```

and after that 

```
sudo /etc/init.d/gdm start
```

---

### Post by illuminati11_13 on 2007-04-26
Thank you. 

I was able to use apt to reinstall x, the gdm and gnome and then repair most of the system using synaptic.

The only noticeable problem I have now is that the fonts in Nautilus seem to be broken. No other program seems to have this problem, but all of the menus and icons in nautilus display rows of boxes instead of letters. When I open up nautilus as root there does not seem to be a problem. I'm not sure how to fix this.

Any help is appreciated.

---

### Post by cqnunez on 2007-04-26
I have also changed the source.list to that of Feisty from Dapper and it worked on one computer. When I tried it on another computer i fot the ff:

====================

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up xfonts-scalable (1.0.0-6) ...
Invalid string keyword: chassis-type
Valid string keywords are:
  bios-vendor
  bios-version
  bios-release-date
  system-manufacturer
  system-product-name
  system-version
  system-serial-number
  baseboard-manufacturer
  baseboard-product-name
  baseboard-version
  baseboard-serial-number
  baseboard-asset-tag
  chassis-manufacturer
  chassis-version
  chassis-serial-number
  chassis-asset-tag
  processor-manufacturer
  processor-version
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exit
dpkg: error processing xfonts-scalable (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 xfonts-scalable
E: Sub-process /usr/bin/dpkg returned an error code (1)

===================

Now when I log on, letters are replaced by blank boxes. I can't open even the Home directory. I'm only able to recognize the applications by the icons beside them. I hope someone can help.

Thanks.

---

### Post by zvacet on 2007-04-27
Are you runing Feisty now? if you are simply change your source list with this or some other

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by cqnunez on 2007-04-27
I already changed it and I think that was how I got the problem. :(

---

### Post by cqnunez on 2007-04-27
And now the desktop is as shown in the picture. Please take note that there are boxes instead of letters. :(

---

