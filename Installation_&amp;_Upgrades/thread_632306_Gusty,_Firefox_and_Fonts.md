---
title: "Gusty, Firefox and Fonts"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by sg3524 on 2007-12-05
I have been searching for a solution, but simply not finding it.

Installed Gusty on both work and home PC's and all is well.  Using Emerald Themes, and have desktop effects enabled, again all is well.

On both machines (home is fresh install - I had an extra hard drive) my fonts display wonderfully everywhere except in Firefox.  In Firefox browser screen (not menus or title bar) MS fonts are jagged and really look poor.  I have installed the microsoft fonts, set my screen to 96dpi as well as trying a few other tricks I have seen posted.

EDIT NOTE: When I first posted this question, I was only using MS fonts in Firefox for web pages.  I susequently found that MS fonts looked bad no matter where I used them.  Problem seems to be centered around MS fonts as all others look very good.  Possible solution  posted a couple of posts down...  

Nothing seems to correct this problem.  I feel like I am missing something here.  I don't want to over ride fonts specified in web pages as I am a web developer and really need to see the fonts as set by the html and css.

Any hints or ideas?  All my favorite tools are in Firefox, so don't want to switch that out.  Is there a way to correct the font rendering quality in the firefox browser screen?

Perhaps some obscure firefox setting that can help to correct?  Maybe in a configuration file for firefox?

Gram

---

### Post by Justin Trouble on 2007-12-13
I have the same problem as you, and I just about to start looking for a solution.

---

### Post by sg3524 on 2007-12-13
Well....

Very interesting development.  /etc/fonts/local.conf will include /etc/fonts/msfonts-rules.conf if it exists, and ignore it if it does not exist.  There are already some hinting rules being applied to MS fonts in alias.conf....  So decided to see what would happen if I removed msfonts-rules.conf.

I renamed msfonts-rules.conf to msfonts-rules.conf.bak:
```

cd /etc/fonts
sudo mv ./msfonts-rules.conf ./msfonts-rules.conf.bak

```

This way I could restore the file if it blew something up.

REstarted X (crtl-alt-backspace), logged back in and Viola!  The MS fonts now look good in all applications including Firefox.  They are displaying just as they do in my Windows IE (on VMware).

So I need to do a little more digging, but this is very telling.  The msfonts-rules.conf may be causing this problem but not sure yet why, or if it is really needed.

FWIW...  After spending time with the MS fonts, found they looked bad no matter where they were used not just Firefox.  This resolved the problem everywhere.

Gram

---

### Post by NilsE on 2007-12-13
Interesting, my fonts have always been good and now I may know why,  

I do not have a msfonts-rules.conf anywhere.  

This is a fresh install of Gutsy with the restricted extras installed which includes MS fonts, codecs, etc..  I wonder if how the MS fonts are installed determines if the config file is created or not.

---

### Post by sg3524 on 2007-12-13
Does your copy of local.conf conditionally include the msfonts-rules.conf file?

Thats a really interesting idea....

Gram

---

### Post by NilsE on 2007-12-13
I have no local.conf and the 51-local.conf has a handle for a missing local.conf.

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- /etc/fonts/conf.avail/51-local.conf file to configure system font access -->
<fontconfig>
	<!-- Load local system customization file -->
	<include ignore_missing="yes">local.conf</include>
</fontconfig>

---

### Post by sg3524 on 2007-12-13
I went back and took a look at my Fiesty backup.  Nothing in fonts but fonts.conf and fonts.dtd

On my work computer (which also has msttcorefonts installed) almost the same, and no msfonts-rules.conf or local.conf.

Somehow I aquired msfonts-rules.conf during the new install of Gutsy at home.  It was a fresh install.

msttcorefonts was installed from System->Administration->Synaptic package manager

Unfortunately, did a lot of stuff during the install.  Not sure if something else could have affected this.

Gram

---

### Post by NilsE on 2007-12-13
> **sg3524 said:**
> 

msttcorefonts was installed from System->Administration->Synaptic package manager

Gram

That may be the answer.  

I installed it with Synaptic also but I did it with the ubuntu-restricted-extras package not the msttcorefonts package.

---

### Post by Justin Trouble on 2007-12-14
I don't have a msfonts-rules.conf.

However I did find the answer to my particular problem with fonts in Firefox at [http://ubuntuforums.org/showthread.php?t=4456](http://ubuntuforums.org/showthread.php?t=4456) by turning on auto hinting.

I discovered the problem to be particularly with web pages that used the Helvetica font, which looked very ugly and blocky when rendered.

---

### Post by mayhemt on 2007-12-25
Awesome, that fixed Serif fonts in firefox for me... thanks my friend.

---

