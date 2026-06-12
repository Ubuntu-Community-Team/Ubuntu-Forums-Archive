---
title: "Some firefox fonts look awful"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by michael37 on 2009-03-13
Since upgrade to Jaunty, I noticed that some Firefox fonts look awful.  I haven't quite pinpointed the problem -- it looks like the default fonts (like the ones used on this forum) are fine, but the ones used on the [https://help.ubuntu.com/community](https://help.ubuntu.com/community) look heavily pixelated.  

I have an LCD monitor and (in Preferences/Appearance/Fonts) subpixel smoothing is on.  Plus all the previously suggested tricks like enabling autohint.conf in /etc/fonts/conf.d is on.

---

### Post by nyarnon on 2009-03-13
I suggest you check the fonts installed on your computer, especially you might consider checking/installing the package ttf-mscorefonts-installer it looks like a fallback problem with a font that is non existant.

---

### Post by forumache on 2009-03-13
> **michael37 said:**
> Plus all the previously suggested tricks like enabling autohint.conf in /etc/fonts/conf.d is on.

You can remove the tricks, the link you indicated renders perfectly here, with a default installation.

---

### Post by nyarnon on 2009-03-13
@forumache

He said he upgraded thats hardly a default install.

---

### Post by forumache on 2009-03-13
> **nyarnon said:**
> @forumache

He said he upgraded thats hardly a default install.

I should have expressed myself better. I also upgraded through each and every version since 6.04, without a new installation since 6.04.

What I wanted to say is that I keep the system as close to the mainline distribution, I modify files in my home directory only (as .fonts.conf), but never (almost) in /etc directories. All changes I am *forced* to do in /etc are reported as bugs (we try to make Ubuntu for humans beeings, it should look nice without having the user modify files in /etc). Also, all the changes in /etc are written down, so I will be able to revert to the distribution files once the bug is fixed.

So, yes, my installation is as close as possible to a default installation (although not being one) and also as close as possible to an updated Ubuntu through all the versions since 6.04

But, as I remove all the tricks after the bug are fixed and fonts are looking great, I recommended to michael37 to remove them too. That is, if he remembers what files he modified...

---

### Post by michael37 on 2009-03-13
Yeah, I am into upgrades... this notebook has been through all releases since Feisty.  Most of the stuff is working so far.

Regardless, installing microsoft fonts helps quite a bit, but it didn't resolve all the problems.
(did I not notice the same problem earlier with older versions? or did it just came up in light of DPI changes?)

Copy a screenshot from cnn.com for your attention.  As you can see, the text fonts looks quite good, and the image reflects the subpixel smoothing; but the heading is quite pixelated.

[IMG]http://img17.imageshack.us/img17/3882/screenshot1ito.png[/IMG]

---

### Post by michael37 on 2009-03-13
> **forumache said:**
> I should have expressed myself better. I also upgraded through each and every version since 6.04, without a new installation since 6.04.
<...>
But, as I remove all the tricks after the bug are fixed and fonts are looking great, I recommended to michael37 to remove them too. That is, if he remembers what files he modified...

I clearly don't.  That was two or three versions ago or so.  

If you'd like to help, an ls -l of your /etc/fonts/conf.d directory would be very helpful.

---

### Post by nyarnon on 2009-03-13
@michael37

Glad that did help, what is the remaining issue?

---

### Post by michael37 on 2009-03-13
> **nyarnon said:**
> @michael37

Glad that did help, what is the remaining issue?

Sorry if I wasn't clear.  The font for the heading in the screenshot is still very pixelated.

---

### Post by nyarnon on 2009-03-13
Well that also could be a font issue because the font was blown up to much, what is the font you have defined in firefox as standard font and at what size. What dpi do you use? Take a look at the advanced button of the font settings.

---

### Post by michael37 on 2009-03-13
The DPI is 100.  I've read somewhere on the forums that Jaunty resets the DPI to its liking.

I am not sure I believe that blowing up fonts makes a difference here.  I played with zoom option in Firefox and smooth fonts stay smooth, and jagged fonts stay jagged.

I just checked on another computer still running Hardy -- the same page renders very smooth.  I also made sure that my conf.d and my Firefox "Content" is configured the same.

The standard font is "serif" size 16 on both computers.

---

### Post by nyarnon on 2009-03-13
Well that seems to be reasonable but what does the advanced button reveal for settings for fonts?

---

### Post by forumache on 2009-03-13
> **michael37 said:**
> I clearly don't.  That was two or three versions ago or so.  

If you'd like to help, an ls -l of your /etc/fonts/conf.d directory would be very helpful.

I'm at work right now, I'll post again after 8 hours with the output of ls -l.

---

### Post by Technoviking on 2009-03-13
Seeing something similar.

```
dbasinge@mikebuntu:/etc/fonts/conf.d$ ls -l
total 4
lrwxrwxrwx 1 root root  31 2009-03-12 16:16 10-antialias.conf -> ../conf.avail/10-antialias.conf
lrwxrwxrwx 1 root root  29 2009-03-12 16:16 10-hinting.conf -> ../conf.avail/10-hinting.conf
lrwxrwxrwx 1 root root  36 2009-03-12 16:16 10-hinting-medium.conf -> ../conf.avail/10-hinting-medium.conf
lrwxrwxrwx 1 root root  43 2009-03-12 16:41 10-sub-pixel-rgb.conf -> /etc/fonts/conf.avail/10-sub-pixel-rgb.conf
lrwxrwxrwx 1 root root  43 2009-03-12 16:16 11-lcd-filter-lcddefault.conf -> ../conf.avail/11-lcd-filter-lcddefault.conf
lrwxrwxrwx 1 root root  39 2009-03-12 16:16 20-fix-globaladvance.conf -> ../conf.avail/20-fix-globaladvance.conf
lrwxrwxrwx 1 root root  39 2009-03-12 16:16 20-unhint-small-vera.conf -> ../conf.avail/20-unhint-small-vera.conf
lrwxrwxrwx 1 root root  45 2009-03-12 16:17 25-ttf-arphic-uming-render.conf -> ../conf.avail/25-ttf-arphic-uming-render.conf
lrwxrwxrwx 1 root root  33 2009-03-12 16:18 30-cjk-aliases.conf -> ../conf.avail/30-cjk-aliases.conf
lrwxrwxrwx 1 root root  39 2009-03-12 16:41 30-defoma.conf -> /var/lib/defoma/fontconfig.d/fonts.conf
lrwxrwxrwx 1 root root  36 2009-03-12 16:16 30-metric-aliases.conf -> ../conf.avail/30-metric-aliases.conf
lrwxrwxrwx 1 root root  33 2009-03-12 16:16 30-urw-aliases.conf -> ../conf.avail/30-urw-aliases.conf
lrwxrwxrwx 1 root root  46 2009-03-12 16:17 35-ttf-arphic-uming-aliases.conf -> ../conf.avail/35-ttf-arphic-uming-aliases.conf
lrwxrwxrwx 1 root root  30 2009-03-12 16:16 40-nonlatin.conf -> ../conf.avail/40-nonlatin.conf
lrwxrwxrwx 1 root root  38 2009-03-12 16:17 41-ttf-arphic-uming.conf -> ../conf.avail/41-ttf-arphic-uming.conf
lrwxrwxrwx 1 root root  27 2009-03-12 16:16 45-latin.conf -> ../conf.avail/45-latin.conf
lrwxrwxrwx 1 root root  31 2009-03-12 16:16 49-sansserif.conf -> ../conf.avail/49-sansserif.conf
lrwxrwxrwx 1 root root  26 2009-03-12 16:16 50-user.conf -> ../conf.avail/50-user.conf
lrwxrwxrwx 1 root root  27 2009-03-12 16:16 51-local.conf -> ../conf.avail/51-local.conf
lrwxrwxrwx 1 root root  38 2009-03-12 16:16 52-languageselector.conf -> ../conf.avail/52-languageselector.conf
lrwxrwxrwx 1 root root  42 2009-03-12 16:16 53-monospace-lcd-filter.conf -> ../conf.avail/53-monospace-lcd-filter.conf
lrwxrwxrwx 1 root root  27 2009-03-12 16:16 60-latin.conf -> ../conf.avail/60-latin.conf
lrwxrwxrwx 1 root root  38 2009-03-12 16:17 64-ttf-arphic-uming.conf -> ../conf.avail/64-ttf-arphic-uming.conf
lrwxrwxrwx 1 root root  35 2009-03-12 16:19 64-ttf-thai-tlwg.conf -> ../conf.avail/64-ttf-thai-tlwg.conf
lrwxrwxrwx 1 root root  35 2009-03-12 16:16 65-fonts-persian.conf -> ../conf.avail/65-fonts-persian.conf
lrwxrwxrwx 1 root root  30 2009-03-12 16:16 65-nonlatin.conf -> ../conf.avail/65-nonlatin.conf
lrwxrwxrwx 1 root root  29 2009-03-12 16:16 69-unifont.conf -> ../conf.avail/69-unifont.conf
lrwxrwxrwx 1 root root  41 2009-03-12 16:41 70-yes-bitmaps.conf -> /etc/fonts/conf.avail/70-yes-bitmaps.conf
lrwxrwxrwx 1 root root  31 2009-03-12 16:16 80-delicious.conf -> ../conf.avail/80-delicious.conf
lrwxrwxrwx 1 root root  31 2009-03-12 16:16 90-synthetic.conf -> ../conf.avail/90-synthetic.conf
lrwxrwxrwx 1 root root  47 2009-03-12 16:17 90-ttf-arphic-uming-embolden.conf -> ../conf.avail/90-ttf-arphic-uming-embolden.conf
lrwxrwxrwx 1 root root  45 2009-03-12 16:19 90-ttf-thai-tlwg-synthetic.conf -> ../conf.avail/90-ttf-thai-tlwg-synthetic.conf
-rw-r--r-- 1 root root 959 2008-09-18 10:52 README
```

---

### Post by forumache on 2009-03-13
> **Technoviking said:**
> Seeing something similar.


Have you manually modified files in that area? Or is the ls -l output a "default" one?

I'll get home soon and compare with my output.

---

### Post by Technoviking on 2009-03-13
> **forumache said:**
> Have you manually modified files in that area? Or is the ls -l output a "default" one?

I'll get home soon and compare with my output.

Should be default.

---

### Post by forumache on 2009-03-13
Interesting.

On my home computer, I have 10-no-sub-pixel.conf and 70-no-bitmaps.conf 
links.

You have the one with sub-pixel and with bitmaps.

I even removed fontconfig-config and reinstalled it, same configuration.

The rendering is fine here.

These differences may explain what you see.

---

### Post by Technoviking on 2009-03-13
> **forumache said:**
> Interesting.

On my home computer, I have 10-no-sub-pixel.conf and 70-no-bitmaps.conf 
links.

You have the one with sub-pixel and with bitmaps.

I even removed fontconfig-config and reinstalled it, same configuration.

The rendering is fine here.

These differences may explain what you see.

The updates today fixed my problem.

---

### Post by michael37 on 2009-03-14
@nyarnon: don't think it matters, the cnn.com website is using its own fonts.

@forumache: umm.  can't imagine myself with no-sub-pixel on the LCD in the 21st century :)

@Technoviking: upgrade did not solve the problem.

Regardless, I removed fontconfig and fontconfig-config (what a creative and telling name!) with --purge option and reinstalled them.  After that, I made no modifications to conf.d directory.  
Instead, following forumache's advice, I created my own .fons.conf, see it below.  

Reboot, and the problem is fixed.  Still not sure what it was -- maybe something about Arial font (I think that's what CNN uses) in conf.d directory?

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
<!--  Enable sub-pixel rendering --> 
  <match target="font">
    <edit name="rgba" mode="assign"><const>rgb</const></edit>
  </match>
</fontconfig>

```

---

### Post by forumache on 2009-03-14
> **michael37 said:**
> 
@forumache: umm.  can't imagine myself with no-sub-pixel on the LCD in the 21st century :)


no-sub-pixel applies only to the login screen. This is how the package is configured. As soon as the user logs in, the personal preferences of that user will be taken into account: I have subpixel rendering activated in Gnome: System|Preferences|Appearance|Fonts|Subpixel Smoothing (LCD) and it looks great without entering any line of text in .fonts.conf or somewhere else.

Just the default installation settings with proper options selected from menu. This is how it should work, anything requiring manual file editing *is* a bug and *should* be reported as such.

---

### Post by michael37 on 2009-03-14
> **forumache said:**
> no-sub-pixel applies only to the login screen. This is how the package is configured. As soon as the user logs in, the personal preferences of that user will be taken into account: I have subpixel rendering activated in Gnome: System|Preferences|Appearance|Fonts|Subpixel Smoothing (LCD) and it looks great without entering any line of text in .fonts.conf or somewhere else.

Just the default installation settings with proper options selected from menu. This is how it should work, anything requiring manual file editing *is* a bug and *should* be reported as such.

Gnome doesn't allow to enable autohinting.  Do you think that is a bug?

---

### Post by Yashiro on 2009-03-15
Try setting the dpi in Firefox to match your desktop dpi.

layout.css.dpi is the about:config key. This had to be done on my old machine with an Opensolaris install a few months ago.

---

### Post by michael37 on 2009-03-16
> **Yashiro said:**
> Try setting the dpi in Firefox to match your desktop dpi.

layout.css.dpi is the about:config key. This had to be done on my old machine with an Opensolaris install a few months ago.

set to default integer -1

what does that mean?

---

### Post by taavikko on 2009-03-16
> **michael37 said:**
> set to default integer -1

what does that mean?

[http://kb.mozillazine.org/Layout.css.dpi](http://kb.mozillazine.org/Layout.css.dpi)

---

### Post by Yashiro on 2009-03-16
Set it manually to match the dpi you have set in your appearance panel. Most people have this at 96.

---

### Post by Götz on 2009-03-17
I thing this is bug [https://bugs.launchpad.net/ubuntu/jaunty/+source/fontconfig/+bug/305394](https://bugs.launchpad.net/ubuntu/jaunty/+source/fontconfig/+bug/305394)

I have downgraded fontconfig, fontconfig-config and libfontconfig1 to version 2.6.0-1ubuntu5 (also the Intrepid version works) and everything looks nice again.

---

### Post by jslinux on 2009-03-17
Definitely a bug. 

All defaults here, but cnn titles and [https://help.ubuntu.com/community](https://help.ubuntu.com/community)
are pixelated

---

### Post by Kow on 2009-03-17
I have the same issue when using the Microsoft fonts... but I don't use the Microsoft fonts anymore. In fact, even when the MS fonts look right the google android & liberation fonts still win.

---

### Post by jmmL on 2009-03-17
I started experiencing this bug yesterday, but it was fixed for me here: [http://ubuntuforums.org/showpost.php?p=6909837&postcount=7](http://ubuntuforums.org/showpost.php?p=6909837&postcount=7)

---

### Post by dirtylobster on 2009-03-17
> **jmmL said:**
> I started experiencing this bug yesterday, but it was fixed for me here: [http://ubuntuforums.org/showpost.php?p=6909837&postcount=7](http://ubuntuforums.org/showpost.php?p=6909837&postcount=7)

Works for me!

---

### Post by jslinux on 2009-03-17
confirmed here, thanks for the fix.

---

### Post by Benjamin_Lebsanft on 2009-03-18
Fixed it for me too, thanks :)

---

### Post by SketchyClown on 2009-03-18
> **jmmL said:**
> I started experiencing this bug yesterday, but it was fixed for me here: [http://ubuntuforums.org/showpost.php?p=6909837&postcount=7](http://ubuntuforums.org/showpost.php?p=6909837&postcount=7)

jimmL,

Thank you very much for this fix. I was finding so many pages looking pixelated.

Digg was so bad I almost couldn't even stand to read it.

Now everything looks fab!

Cheers!

---

