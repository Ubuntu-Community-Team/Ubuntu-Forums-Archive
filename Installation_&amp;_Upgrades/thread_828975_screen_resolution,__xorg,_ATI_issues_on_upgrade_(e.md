---
title: "screen resolution,  xorg, ATI issues on upgrade (every upgrade...)"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by gratefulfrog on 2008-06-14
This is a summary post to help others who may have some or all of the following issues after upgrading:

[LIST]
[*]xorg.conf file lost
[*]Desktop screen resolution broken
[*]Gnome Screen Resolution tool broken
[*]Login Screen resolution borken
[*]ATI drivers lost (free or fglrx)
[/LIST]

I had all these problems after my Hardy upgrade on AMD64. Now, a mere 6 hours of work later, it's all working! 

I've attached my xorg.conf and /var/log/X.log.0 files to help those who may be as confused as I was.

Here's what I did:
1. look for help:
These references were **very helpful**:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

2. create a xorg.conf file:
```
$sudo dpkg-reconfigure xserver-xorg
 
```
my current xorg.conf file is attached.

3. followed all the advice in the Fix Video Resolution How-To
4. Followed all the advice in the Open Source ATI Driver How-to.
5. set the Gnome default resolution using gconf-editor;
as normal user:
```
$ gconf-editor
```
navigate to ```
desktop/gnome/screen/default/0
```
set values to what you want as per screen-shot in attached file.

[IMG]http://picasaweb.google.co.uk/gratefulfrog/Ubuntu/photo#5211737117386433922[/IMG]

6. Restart Xserver properly:
[INDENT][LIST=1]
[*]CTRL-ALT-backspace,
[*]Ctrl-Alt-F1,
[*]then:
```
$ sudo /etc/init.d/gdm restart
```
[/LIST][/INDENT]

This should work for you, if you put the correct values in the various sections in the xorg.conf file, and if you are very patient.

Good Luck,
GF

---

### Post by Jophish on 2008-06-14
Oh darn, My card is a Radeon X1950 AGP, of the RV570 type, not on any list, supported or unsupported. I just with there was some guide like this for getting the fglrx driver to work with my system!

---

### Post by gratefulfrog on 2008-06-14
Is this card: > X1950 AGP, of the RV570 type

not a derivative of the 1900 series?

Have you tried to use the ATI open source drivers? If not, give it a shot and you might be surprised at the performance. 

I used to use the fglrx drivers but have switched to the free ones since they perform much better now. The more people who use the free software, the better it gets!

Don't despair! ;-)
GF.

---

### Post by Jophish on 2008-06-14
I'm sorry to report, that after installing those drivers I still manage to get a white screen on compiz starting. I'm going to give the fglrx drivers another shot at installation.

---

### Post by gratefulfrog on 2008-06-14
> **Jophish said:**
> on compiz starting. 

do you need compiz? why not just use gnome?

---

### Post by Jophish on 2008-06-14
Well, the features looked quite nice, and I'm sure that it would be a nice thing to have. I'm also looking to being able to run any 3D application really.

---

### Post by gratefulfrog on 2008-06-14
What I mean is, why not try to get it running with gnome first, then see where the issues are with compiz... Surely gnome will be able to work with the ati free drivers, then you can try to get compiz working step by step, particularly don't forget the "composite" line at the end of the xorg.conf file.

In any case, keep posting until someone with real knowledge helps!
ciao,
GF

---

### Post by Jophish on 2008-06-14
Oh, you misunderstand me, I have gnome working fine. Its only compiz that whites out.

When I run glxinfo, It says that I have no direct rendering. Could this be of any use?

---

### Post by gratefulfrog on 2008-06-14
> **Jophish said:**
> I have no direct rendering. Could this be of any use?

Indeed, you probably need direct rendering.

Have you carefully followed: [https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")
?

Can you play the game: 'neverball' smoothly? That's a good test of your graphics acceleration. Install it and try it as a test. 

Compare your /etc/X11/xorg.conf file to mine (attached to original post) and see if you can't change an option to get it to work?

Also, check /var/log/X/log/0 file: scan for lines that start with (EE) or (WW) ,i.e. errors or warnings, to give you a hint as to what's wrong in the Xserver startup.  Be sure to properly restart the xserver each time (see my original post) you tweak the xorg.conf file.

This should be repairable. Sorry to say that I'm off for today. I'll be around tomorrow though.

Never give up.

---

