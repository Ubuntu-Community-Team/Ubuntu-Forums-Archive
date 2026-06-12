---
title: "issue installing bioshock with playon linux."
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by 00Disco on 2011-07-01
can some one help me get this game installed?  it keeps getting stuck on downloading patch.  Please help.

---

### Post by MAFoElffen on 2011-07-01
> **00Disco said:**
> can some one help me get this game installed?  it keeps getting stuck on downloading patch.  Please help.
I've seen this here, read but unanswer...  Thought maybe a moderator here would move it to a forum where it would, but...

Tip-  Your Ubuntu Linux system does seem to be running and your want help installing a game.  Where you need help would probably be better answered in either Ubuntu's "Games and Leisure" Forum or Ubuntu's "Wine" Forum.  Since Bioshock is a Windows game, probably better addressed in the "[Wine]("http://ubuntuforums.org/forumdisplay.php?f=313")" Forum... Where someone there might have not just experience installing it under Wine, but also some tips for tweaking and tuning it in Wine to run / play better.

A lot of Gamer's who run Windows games under Wine visit the Wine Forum to share tricks and ask questions.  A lot of gamers who are using and playing Linux games, visit the Games and Leisure Forum.

Just a thought... 

That said, here are the instructions installing Bioshock under wine:
> **_How To Get BIOSHOCK Running _**(Under Wine)
Install the game in the normal way by inserting the disk into the drive and running the setup.exe with Wine (or by downloading the STEAM version).

Once the game is installed the following steps need to be taken to ensure that it runs correctly (by running the code below in a terminal) :-
```

wget http://www.kegel.com/wine/winetricks

```Install the vcrun2005 winetricks package (by running the code below in a terminal) :-
```

sh winetricks vcrun2005

```Once this has been done, add the following DLL overides to the Libraries tab of your wine.cfg :-
```

msvcp80 (native)
openal32 (native0

```Make sure that in the Audio tab of winecfg you have the **ALSA** driver selected as your audio driver.
Also make sure that your wine version is set to XP.  It is best to run the game in a wine window.  Set the resolution to **1366x768** in the graphics tab of Wine.  In game set Textures and other options to **Medium**.

The game will now run.There are some known issues for some with fixes... Look at the bottom of this page:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9320](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9320)

---

