---
title: "Kernel Panic on boot load"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by decipher on 2008-10-13
Howdy all

I'm relatively new to linux and have been loving the Ubuntu experience.
Recently I've been checking out the other distro's and decided to give Fedora a try.

I installed Fedora, which took over my grub boot menu, which meant I could not load Ubuntu. :( From within Fedora, I can see my partitioned drive that contains Ubuntu.

OK so basically I took the boot drive details from my ubuntu menu.lst file and put them in Fedora's grub.conf file.
I also changed Fedora's **default** value as well as commenting out the **splashimage** and **hiddenmenu** lines within the grub.conf file. 

So, now the previous ubuntu grub menu loads, I select the ubuntu version I wish to load, the ubuntu splash screen displays, the loading bar goes back and forth, and then freezes.

I reboot, wait for the grub menu to load, highlight the Ubuntu option, press e and edit the kernel entry, to remove the "**quiet**" and "**splash**" options so i can see whats going on. Press b to boot and now linux is telling me what it's trying to load. ... loads drivers and wot not, but gets to a point and freezes:
```
/init: /init: 184: cannot open /root/dev/console: No such file
... Kernel panic - not syncing: Attempting to kill init!
```

Ubuntu (Hardy) loaded just fine before I stuck fedora on there. I've given up, i'm beat, i'm not sure what else I can do to resolve this, other than fresh ubuntu install. 
Any suggestions? :popcorn:

---

### Post by WWSmith36 on 2008-10-13
Its ok to allow Fedoras grub to handle the booting.  I would restore whatever edits you did to fedoras boot menu and then add this line for ubuntu

I would recommend booting ubuntu with a with this type of edit which will call ubuntus menu.lst file

```
title          Ubuntu Hardy
configfile     (hdx,y)/boot/grub/menu.lst
```

where (hdx,y) is your Ubuntu partition.  
If Ubuntu was installed with a separate boot partition, you should use that for (hdx,y) and take the ¨/boot¨ out of the menu.lst path.

This type of setup with a configfile allows ubuntu to run with the latest kernel without you having to manually edit anything - It will be done automagically.

If you have trouble finding your which partition is what, remember you can always have grub help you.

```
grub> find /boot/grub/stage1
grub> find /grub/stage1
```

Hope this helps

---

### Post by decipher on 2008-10-14
Thank you WWSmith36, I'm going to give this a bash this evening and will post back the outcomes.

---

### Post by decipher on 2008-10-17
Sorry for the delay in posting back.
I restored  fedora's /etc/grub.conf, and added the configfile path for ubuntu's menu.lst.
Unfortunately when I boot into ubuntu it still freezes at the same point.
Not sure what I did to break ubuntu, in any case I don't like fedora very so I might just format the harddrive and stick a fresh ubuntu on there, I don't use this laptop for anything (other than playing with linux) so it's all good.

---

