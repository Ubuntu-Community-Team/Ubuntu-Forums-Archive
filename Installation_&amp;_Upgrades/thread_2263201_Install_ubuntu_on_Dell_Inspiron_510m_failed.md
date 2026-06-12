---
title: "Install ubuntu on Dell Inspiron 510m failed"
date: 2015-01-30
forum: Installation &amp; Upgrades
---

### Post by memeese on 2015-01-30
Hello, 
I´ve got a Lap Top with ubuntu on it for Years now, and recommended it to my friend. I told him I wold make it run on his Laptop for on mine it was quite easy to install (ThinkpadSL510) but now I face a for me unsolveable Problem...
I tried to install Ubuntu LTS version on my friends old Laptop, but failed. There was said : 
***
This kernel requires the following feature not present on your CPU: pae

Unable to boot- please use a kernel appropriate to your CPU
***
I found some advice as to instal from a Flashstick, but am unable to understand them...

***
**USB-Flashstick mit grub-mkconfig einrichten**

 
[LIST=1]
[*]Einen USB-Flashstick (1 GiB oder groesser) mit FAT32 formatieren. Es  wird angenommen, der USB-Flashstick ist unter &#8220;/media/usbstick/&#8221;  eingebunden und als &#8220;/dev/sdc/&#8221; gemountet. 
[*]Bootloader Grub auf den Stick schreiben:  [TABLE]
[TR]
[TD="class: line_numbers"]1[/TD]
[TD="class: code"][COLOR=#c20cb9]**sudo**[/COLOR] grub-install [COLOR=#660033]--no-floppy[/COLOR] [COLOR=#660033]--root-directory[/COLOR]=[COLOR=#000000]**/**[/COLOR]media[COLOR=#000000]**/**[/COLOR]usbstick [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]sdc[/TD]
[/TR]
[/TABLE] 
[*]Generieren der Grub-Konfigurationsdatei:  [TABLE]
[TR]
[TD="class: line_numbers"]1[/TD]
[TD="class: code"][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**bash**[/COLOR] [COLOR=#660033]-c[/COLOR] [COLOR=#ff0000]"grub-mkconfig > /media/usbstick/boot/grub/grub.cfg"[/COLOR][/TD]
[/TR]
[/TABLE] 
[*]Im File &#8221; /media/usbstick/boot/grub/grub.cfg&#8221; die &#8220;menuentry{ &#8230; }&#8221;-Abschnitte ersetzen durch: 
[/LIST]
  [TABLE]
[TR]
[TD="class: code"]menuentry [COLOR=#ff0000]"Lubuntu 12.10 for non-PAE Systems"[/COLOR] [COLOR=#7a0874]**{**[/COLOR]
  [COLOR=#007800]iso_path[/COLOR]=[COLOR=#000000]**/**[/COLOR]lubuntu-[COLOR=#000000]12.10[/COLOR]-desktop-i386.iso
  [COLOR=#7a0874]**export**[/COLOR] iso_path
  search [COLOR=#660033]--set[/COLOR] [COLOR=#660033]--file[/COLOR] [COLOR=#007800]$iso_path[/COLOR]
  loopback loop [COLOR=#007800]$iso_path[/COLOR]
  [COLOR=#007800]root[/COLOR]=[COLOR=#7a0874]**(**[/COLOR]loop[COLOR=#7a0874]**)**[/COLOR]
  configfile [COLOR=#000000]**/**[/COLOR]boot[COLOR=#000000]**/**[/COLOR]grub[COLOR=#000000]**/**[/COLOR]loopback.cfg
  loopback [COLOR=#660033]--delete[/COLOR] loop
[COLOR=#7a0874]**}**[/COLOR][/TD]
[/TR]
[/TABLE]

  
[LIST=1]
[*][lubuntu-12.10-desktop-i386.iso]("http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/lubuntu-12.10-desktop-i386.iso") (695 MiB) in die oberste Ebene des USB-Flashsticks kopieren. 
[*]USB-Flashstick sicher entfernen. 
[*]Das entsprechende System von diesem Flashstick booten und ueber  &#8220;Lubuntu 12.10 for non-PAE Systems&#8221; normal installieren. Die angebotene  gleichzeitige Aktualisierung wegen des Kernel-Problems an dieser Stelle  ablehnen. 
[*]Nach dem ersten Boot die Kernel-Pakete *vorerst* per apt-pinning vom Aktualisieren ausschliessen. 
[*]Das System aktualisieren. 
[/LIST]

***
I do understand WHAT I am to do but do not know HOW =(

is anyboy able or has the time and spirits to help me? 
Please!

(I am sorry for my english is maybe not as good as I expected it to be, so sorry for mistakes in writing or else...)



**************
Well, I anaged to Install an old ubuntu version. Probably that works because the pae is not "asked" there...
Now there is the 8.04 on, but if I want to update the new ubuntu versin is says:
********

   W:Konnte [http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/binary-i386/Packages.gz](http://ports.ubuntu.com/ubuntu-ports/dists/lucid/main/binary-i386/Packages.gz) nicht holen  404 Not Found  
 , E:Einige Indexdateien konnten nicht heruntergeladen werden, sie wurden ignoriert oder alte an ihrer Stelle benutzt.

*********

After all I solved the Problem!!!
On This link you´ll find the version 12.04from ubuntu as none pae version (lines 93-100 alresdy cleared) .
It works great as normally expected from ubuntu and is as easy as installing on a pae supported PC.

[FONT=&amp][http://www.heise.de/open/artikel/Ubuntu-12-04-4-fuer-alte-Rechner-2152983.html](http://www.heise.de/open/artikel/Ubuntu-12-04-4-fuer-alte-Rechner-2152983.html)[/FONT]

---

### Post by mörgæs on 2015-01-31
Hi,welcome to the fora.

Best you can do is installing Lubuntu 14.04.1 or 14.10 using the  forcepae setting.
[https://help.ubuntu.com/community/PAE/](https://help.ubuntu.com/community/PAE/)

---

### Post by lorent on 2015-02-17
Edit : too fast, i should have read the answer from [**[COLOR=#C61919][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075"), the solution was in it…

I have exactly the same problem. It seems that Ubuntu is not compatible with non PAE processor since Ubuntu 11. I'll try to install it soon and upgrade it to ubuntu 12 (should be possible from what i've found)

---

