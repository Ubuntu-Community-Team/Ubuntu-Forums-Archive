---
title: "Upgrade 9.10 to 10.04 - no window borders, no buttons, ..."
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Moustaffa on 2010-05-03
Hey guys,

I upgraded to 10.04 but problems started very quickly:

I can see my desktop but when I start an application, there are no window borders or buttons to close/minimize that application! They just vanished.

Also, opened windows don't appear on the taskbar, so I can't switch between windows, not even with ALT + TAB.

The mouse isn't an arrow anymore, but a dark cross :s


Some specifications:
Dell vostro 1000, ATI Radeon IGP Xpress 1150 (128mb shared), AMD64 Turion

Here is what I did during the upgrade: everything default, except for once, when it asked me what to do with menu.lst (keep the old one or replace it with the newer version) I chose "replace" (default was to keep the old one). Can that be the reason?
On another forum someone thought the issue was with my graphics card.

What do you think?

---

### Post by wekebu on 2010-05-03
I think this is a similar problem on other threads (that I can't locate right now).  You can temperarly fix by going into System> Preferences> Appearance> Visual Effects.  You probably have None right now?  Change it to either of there other choices.

The problem is this setting will default back to None on your next reboot.

---

### Post by Mazin on 2010-05-03
If you make a new account, does the new account still have this problem?  If not, it means that your settings files are causing the problem.  In your home folder, choose Show Hidden Files, and you can see the dot files that are your settings.  You can move some of these dot files to another safe place as backup, and when you logout and login again, they will be recreated with correct default options.

---

### Post by Moustaffa on 2010-05-03
In the meanwhile I've installed 9.10 again, but before trying to upgrade again I want to gather as much info as possible.

I should also say that I tried a clean install from a burnt cd, but this also didn't work!!
The thing is that the cd boots and I get the welcome screen (where you have the options of booting from cd, installing, testing for bugs, ...) but no matter what I choose, it stays on that same screen. The cd starts spinning for a bit but then simply stops again.
This same problem also occurs when I try to install it in VMware, it stays on that screen!

---

### Post by byline on 2010-05-03
> **wekebu said:**
> I think this is a similar problem on other threads (that I can't locate right now).  You can temperarly fix by going into System> Preferences> Appearance> Visual Effects.  You probably have None right now?  Change it to either of there other choices.

The problem is this setting will default back to None on your next reboot.
In our case, it hasn't. Hubby changed the settings so that our windows show as they previously did under 9.10. We power down the computer every night. When we reboot in the morning, all the window settings are as he fixed them.

---

### Post by Moustaffa on 2010-05-03
By the way, I'm trying the alternate installer ([http://releases.ubuntu.com/lucid/ubuntu-10.04-alternate-amd64.iso](http://releases.ubuntu.com/lucid/ubuntu-10.04-alternate-amd64.iso)) in VMware as we speak. I'll post my results when I'm done.

---

### Post by Moustaffa on 2010-05-03
Ok, I tried installing the 64 bit version of Lucid Lynx and I've encountered a new problem: I can't type anything in the login screen!

The setup goes flawlessly, no errors, nothing. When it asked me to choose a password I entered one, so my keyboard was working then.
But after the installation when it booted to the login screen, I couldn't login because I can't type anything :s I tried to change the keyboard language but no help, I simply can't login...

Anyone who knows why this is happening?

---

### Post by Moustaffa on 2010-05-03
Nobody?

---

### Post by Rosemachinegun on 2010-05-03
I had this problem when I upgraded to Lucid on my desktop. In my case, I think compiz hadn't started. Properly launching it solved it for me.

---

### Post by Moustaffa on 2010-05-04
> **Rosemachinegun said:**
> I had this problem when I upgraded to Lucid on my desktop. In my case, I think compiz hadn't started. Properly launching it solved it for me.

Could you repeat your answer? I'm not fully understanding it. What about compiz? How can it really matter for an upgrade?

Greets

---

### Post by KinKiac on 2010-05-05
Were you by any chance using Emerald as your window decorator before the upgrade?  Ive seen issues with Emerald before where it didnt seem to like the upgrade so it had to be removed and re-installed after upgrade to get the window borders back.  Either that or you could use the Compiz Icon and just reload the window manager or switch back to GTK from emerald or vice versa?

---

### Post by Rob T on 2010-05-08
yeah ive got the same problem with my laptop, when i start it no window borders apear but can be easily fixed with the visual effects as someone mentioned earlier and is on no visual effects, but if it is switched to either of the other options and switched back it is fine :s my guess is something isnt starting properly, such as compiz

---

### Post by Rob T on 2010-05-08
ive managed to fix the problem, when i booted up my laptop compiz wasnt running, clicking on the compiz icon in the aplications menu brought it back to normal again.  

so to solve it go into system > preferences > startup aplications and add a new program, with whatever name your want and the comand:
compiz

restart your computer and see if its worked, as it did for me

---

### Post by twid on 2010-05-08
Yes, the problem is that compiz is not starting. Other accounts on my computer using gnome-wm work OK.

Solution: The startup script seems to invoke compiz.real and not compiz.

So you can fix this by

```

cd /usr/bin
sudo ln -s compiz compiz.real

```

---

### Post by mc_cappy on 2010-05-13
**@twid** thanks a million times :)

---

### Post by WinRiddance on 2010-05-29
**Window borders also work new without restarting or logging off ...**

If you have the compiz fusion icon installed, located under system tools from the start menu, just click on it. When the compiz symbol appears on your screen go ahead and right click on it, followed by selecting _reload window manager._
Presto, a couple of seconds later you'll have your borders back.
If you're not using compiz with window borders, then I don't know what else to tell you, sorry.

---

### Post by SergeyR on 2010-07-24
> **Moustaffa said:**
> Hey guys,

I upgraded to 10.04 but problems started very quickly:

I can see my desktop but when I start an application, there are no window borders or buttons to close/minimize that application! They just vanished.

...

What do you think?

I had the same problem. Removing old config helps.

Just type this in gnome-terminal
**[FONT=Courier New]mv  .gconf/desktop/ .gconf/_desktop[/FONT]**
and then logoff and login again.

---

### Post by mfarshada on 2011-11-08
> **twid said:**
> Yes, the problem is that compiz is not starting. Other accounts on my computer using gnome-wm work OK.

Solution: The startup script seems to invoke compiz.real and not compiz.

So you can fix this by

```

cd /usr/bin
sudo ln -s compiz compiz.real

```

It solved the problem perfectly for me. 
I had Emerald & compizconfig-settings-manager installed before upgrading. Hope somebody reports the bug.

---

### Post by nothingspecial on 2011-11-08
Please don't bump old threads to the top.

Closed.

---

