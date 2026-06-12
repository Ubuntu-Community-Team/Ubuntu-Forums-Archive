---
title: "G. Gibbon Flash/Youtube"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Nathan Otis on 2007-10-25
Ok, so I've been searching around but nothing I found about installing flash seems to get videos going in Youtube. Here's the very polite message youtube gave me today (after the Gibbon upgrade (things worked in Feisty)

**Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.**

Help a brother out?
n.

---

### Post by Nathan Otis on 2007-10-25
Oh! Both Java and Javascript are enabled in Firefox.
n.

---

### Post by kerry_s on 2007-10-25
is gutsy using firefox 2.0.0.8?
if so, it's a flash problem.
the fix is to install flash 7.
grab the flash i attached, unpack it and put the whole plugins folder in your .mozilla folder(nautilus ~/.mozilla)
restart firefox and give it a try.

---

### Post by Nathan Otis on 2007-10-25
The perfect solution. It was easy and it worked. Thank you.

n.

---

### Post by kerry_s on 2007-10-25
> **Nathan Otis said:**
> The perfect solution. It was easy and it worked. Thank you.

n.

hey, you can reinstall the flash-nonfree. it still works with both flash versions installed and the flash 9 sites will still work. it seems if the site is flash 7 compatible it will use that and if the site needs flash 9 that will be used. the best of both. :)

---

### Post by pt123 on 2007-10-26
I just went to the Cnet Videos site and its giving me this message, I installed flashplugin non free using synaptic. Never had this problem in Feisty.

But the site is working fine on Epiphany. 


We've detected that you need to upgrade or install Flash 8 or later to view CNET TV and our library of thousands of tech videos. Installing Flash is fast, free, and easy! Simply follow the instructions from your browser, or click here to install/upgrade the free Flash player.
 
Thanks,
The CNET TV Team

---

### Post by kerry_s on 2007-10-26
> **pt123 said:**
> I just went to the Cnet Videos site and its giving me this message, I installed flashplugin non free using synaptic. Never had this problem in Feisty.

But the site is working fine on Epiphany. 


We've detected that you need to upgrade or install Flash 8 or later to view CNET TV and our library of thousands of tech videos. Installing Flash is fast, free, and easy! Simply follow the instructions from your browser, or click here to install/upgrade the free Flash player.
 
Thanks,
The CNET TV Team

hey your right, it's not working for me now. cnet was 1 of the sites i tested it on earlier and it was working. weird. i'll play with it some more, see if i can't get everything to work. :)

---

### Post by kerry_s on 2007-10-26
i think i found the problem with the flash 9.
in /usr/lib/flashplugin-nonfree
the > libflashplayer.so < is suppose to be executable, so here's what i did.
i moved the plugins folder out of .mozilla then i deleted /.mozilla/firefox/pluginreg.dat
then i
sudo chmod +x /usr/lib/flashplugin-nonfree/libflashplayer.so
to make it executable.

now the flash seems to work right, try giving that a go. sorry for the run around i only installed debian sid this mourning, which has 2.0.0.8, so i'm still weeding through things. good luck.

yeah, that seems to have fixed it for me. i can even listen to pandora radio and watch youtube at the same time. :)

---

### Post by pt123 on 2007-10-26
^ Thanks that worked like a treat

---

### Post by kerry_s on 2007-10-26
> **pt123 said:**
> ^ Thanks that worked like a treat

i just hope it lasts. :confused: :lolflag:

---

### Post by Endolith on 2007-10-27
I have the same problem.  Have you submitted a bug report?

---

### Post by Endolith on 2007-10-28
Look in about:plugins and see if it lists Flash twice (7 and 9).  Mine did.  

I fixed it by: 

1. Removing flashplugin-nonfree completely
2. Remove libflashplayer.so and flashplayer.xpt from ~/.mozilla/plugins
3. Reinstalling flashplugin-nonfree

---

### Post by rcoconnell on 2007-10-28
Ok, this is a total disaster.  Upgraded from Feisty, where YouTube worked just fine, I've tried to annihilate all traces of the flash plugin and reinstall, and *nothing* has worked.  The most thorough version of this is:

1. Quit Firefox
2. Delete the contents of the ~/.mozilla/plugins
3. Delete ~/.mozilla/firefox/pluginreg.dat
4. Do a complete removal of flashplugin-nonfree
5. Reinstall flashplugin-nonfree

When I restart firefox, youtube still doesn't work.

Just for giggles, I've run the flash installer -- that doesn't work either.

What gives?

-R

---

### Post by Endolith on 2007-10-29
What does it say in about: plugins?

---

### Post by dvmrp on 2007-10-31
unfortunately, I'm another one to join the list of this disaster. I did everything above but it still doesn't work.

---

### Post by Krieg on 2007-11-05
Hello guys.   I am part of the club.

---

### Post by Nathan Otis on 2007-11-05
I ended up uninstalling everything and installing version 9 again and it all seems to work.

ymmv.
n.

---

### Post by Endolith on 2007-11-05
> **Endolith said:**
> Look in about:plugins and see if it lists Flash twice (7 and 9).  Mine did.  

I fixed it by: 

1. Removing flashplugin-nonfree completely
2. Remove libflashplayer.so and flashplayer.xpt from ~/.mozilla/plugins
3. Reinstalling flashplugin-nonfree

This fixed my friend's computer, too, by the way, so this particular problem was not unique to me.

---

