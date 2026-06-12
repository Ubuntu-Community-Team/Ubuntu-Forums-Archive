---
title: "Another GRUB issue"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by mattygg on 2011-06-13
Hi all,
 
I have been looking through your forum all night but cant seem to find the answer.
 
I have a dual boot system w7 and ubunutu. When i had version 10.10 (i think) everything was working fine, the grub would select w7 as boot preference.
 
I have, however just updated to 11.04 and i cant get the grub to change its order. I have tried using startupmanager and selecting the second to last one, as per tips and i have also tried all the options. I have also tried editing the grub file, i think its /etc/default/grub. i have also tried grub-customizer but again, this doesnt work.
 
I have noticed however that the options shown arent the same as the options when i boot my system. Im not sure whether i have got two GRUBS installed or something like that. 
 
I have also tried using boot-repair, however this just states that there is no GRUB installed, however as i mentioned, i can read the grub, and so can the programs.
 
Any ideas?
 
Thanks
 
Matt

---

### Post by nzjethro on 2011-06-13
Did you run

```
update-grub
```

I had major issues with my dual boot when I reverted back from 11.04 to 10.10 because I forgot this step.

---

### Post by oldfred on 2011-06-14
Welcome to the forums.

Grub 1.99 has some major changes and some of the gui tools have not caught up. I think startup manager may create a menu.lst and confuse booting? I would for a short time now just edit /etc/default/grub manually until the gui tools catch up.

Grub 1.99 Submenus - drs305
[http://ubuntuforums.org/showthread.php?t=1739336](http://ubuntuforums.org/showthread.php?t=1739336)
LIveCD needs to be 1.99 same version
[http://ubuntuforums.org/showthread.php?t=1751383](http://ubuntuforums.org/showthread.php?t=1751383)

Post boot script:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

