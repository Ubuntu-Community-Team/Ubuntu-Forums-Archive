---
title: "Lots of problems with WINE, Java, and program installation in Gusty"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by Tsukasah on 2008-01-23
I realize that I posted this in "Absolute Beginner Talk" but that was by mistake. I think this is the right place to post something like this, correct?

I'm using a decent spec computer. AMD Athlon x64 4200+ 2.2ghz Dual Core Processor, Gigabyte motherboard(NVIDIA 6200 onboard video, I think), 1gb of RAM. Anyways I recently used just the 32bit Ubuntu with Feisty. After I had a strange problem with WINE and that I couldnt upgrade to Gusty because when it prepared to upgrade it couldnt find some "automatix" file and would then quit trying to upgrade. So I went to the ubuntu site and made me a 62bit Gusty Gibbon live cd, and installed. It looked weird at first, There were no Icons at the top(no ubuntu logo next to applications) and the bottom of hte screen looked like it had orangish tears. I enabled the restricted graphics driver thing, now it all looks fine. After I installed flash on mozilla firefox, I thought I was all good to go. Now no embedded video will work, and here's what youtube looks like [http://s114.photobucket.com/albums/n250/12ed_XIII/?action=view&current=Screenshot-2.png](http://s114.photobucket.com/albums/n250/12ed_XIII/?action=view&current=Screenshot-2.png)

Notice the play/pause section, etc. Also, when I pause the video it wont pay again, and if I watch the full video and hit play to replay it it shows only the first showing image. And some program called "gnash" or something is installed, and when I quit the area where the video should be turns grey.

About WINE. I go to add/remove programs and try to click the check box but it doesn't mark itself, I can't install it. What's going on?

One last thing, how do I install TuxGuitar? Here's what it said in the readme:

INSTALL:
Extract TuxGuitar-*.tar.gz in your favorite location
$tar xfz TuxGuitar-*.tar.gz
$mv TuxGuitar-* /home/*/install_dir

RUN:
Run TuxGuitar script.
$/home/*/install_dir/TuxGuitar-*/TuxGuitar

I extracted TuxGuitar to a folder on my desktop, but after that I dont get the "$tar" part and what the * means. Any help would do! thanks!

Oh, and one minor problem. Sometimes when I highlight text to copy it, and I hit ctrl c, it doesn't always copy, I usually have to right click and hit copy. Nothing that bad, just annoying. Oh, and sorry I typed this post extremely poorly, I just woke up about 30 minutes ago and I'm still really tired :P

:guitar:

---

### Post by zvacet on 2008-01-24
System>administration<software sourcess<chek all boxes under ubuntu software and under updates tab.Reload.You can install Wine with synaptic.For Tuxguitar **read me** tell you to unpack file but you allready did it,so follow instructions after that command.For java,Flash and other

```
sudo apt-get install ubuntu-restricted-extras
```

---

