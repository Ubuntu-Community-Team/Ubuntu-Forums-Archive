---
title: "Upgrade to 12.04 kills gnome-shell."
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by yayramen on 2012-04-27
So Unity kills my PC. Never knew why, but it didn't really bother me, because I didn't like the interface. So I opted for gnome-shell. 

And I upgraded to 12.04 today, and now gnome shell no longer works. 
It logged me into the environment, but I was unable to type the password for the keyring, and the environment itself didn't seem to load. I had basic desktop access, and whatnot, but not enough to do anything with. I had to ctr+alt+f2 and killall -u me gnome-session to get it to log out, so I could log in via Unity to post this. 

Anybody know what's going on? Yes, I uninstalled gnome-shell and reinstalled, still nothing.

I also ran sudo apt-get install -f 
(and sudo apt-get -f install just to make sure I remember right)
and it didn't come up with anything, so I know they upgrade was good. 

What do I need to get my gnome 3 back?

---

### Post by kohoutek1 on 2012-04-27
Hi, Yayramen. 

I'm a pure Gnome-Shell user too. Removed Unity completely. I asked this forum a few days ago if anyone knew of any problems with upgrading to 12.04 from 11.10 with GNOME Shell only. The answer I got was reassuring at the time: No major problems, just some extensions that might not work.

I'll let you know what happens once I finish the upgrade, which is still in progress here.

---

### Post by yayramen on 2012-04-27
Hey, thanks for the reply.

Yeah, thanks to low download speeds, and me torrenting and playing minecraft and all sorts of goofing around, my upgrade took me the better part of the day. But I too, was assured by threads all over that it would be a smooth transition. Unfortunately, it didn't go that way. I have gotten out of unity 2D, and am now in gnome classic, which is close, I suppose.

Another thing I should mention is the custom theme I had (nolo? the ics port for gnome) was compromised in the later parts of the install, with broken icons, and was the same during the upgrade, I had to switch to a different theme whilst booted into unity in order to get to the default ambiance theme.

I was hoping this would have been a smooth transotion >:

---

### Post by kohoutek1 on 2012-04-27
Here's my report on how the installation went here, and it's mixed:

1st, Good news: The install did *not* put Unity on my system. Yay!:guitar: I didn't have it, had removed it, and I was wondering if it would suddenly become default. It didn't.

I rebooted right back into Gnome-Shell, the default, and all applications and documents are intact.

Now, the bad news: NO extensions work. That means all themes are broken too, until I update all my extensions. ](*,)

Yayramen:

Is it possible that GNOME Shell is actually on your system, but that Unity has taken the default?

Did you check using terminal? If not, run this command:

```
gnome-shell --version
```

Output should read:

```

:~$ gnome-shell --version
GNOME Shell 3.4.1

```

---

### Post by kohoutek1 on 2012-04-27
Yayramen,

Your problem may be with conflicting extensions. Just happened to me, too. See this thread: 

[http://ubuntuforums.org/showthread.php?t=1966777](http://ubuntuforums.org/showthread.php?t=1966777)

Reboot into Unity, then delete any extensions you may have in the two directories where they're stored:

(as root) /usr/share/gnome-shell/extensions
~/.local/share/gnome-shell/extensions

You don't need any terminal commands to do this. All extensions are self-contained javascripts.

Then reinstall what's available.

---

### Post by jackson21 on 2012-04-27
Try a fresh install of ubuntu 12.04.
It will save you a lot of troubles, with outdated files 
an the system.
Consider the  short time time  of making a fresh install compared to the woes
of "flogging a dead horse" with outdated libraries!!!!

jackson from /Austria

---

### Post by yayramen on 2012-04-27
> **kohoutek1 said:**
> Here's my report on how the installation went here, and it's mixed:

1st, Good news: The install did *not* put Unity on my system. Yay!:guitar: I didn't have it, had removed it, and I was wondering if it would suddenly become default. It didn't.

I rebooted right back into Gnome-Shell, the default, and all applications and documents are intact.

Now, the bad news: NO extensions work. That means all themes are broken too, until I update all my extensions. ](*,)

Yayramen:

Is it possible that GNOME Shell is actually on your system, but that Unity has taken the default?

Did you check using terminal? If not, run this command:

```
gnome-shell --version
```

Output should read:

```

:~$ gnome-shell --version
GNOME Shell 3.4.1

```

I know I've had Gnome Shell, it let me boot into it, and then I know I had it from the reinstall, so inputting this did spit out 3.4.1

> **kohoutek1 said:**
> Yayramen,

Your problem may be with conflicting extensions. Just happened to me, too. See this thread: 

[http://ubuntuforums.org/showthread.php?t=1966777](http://ubuntuforums.org/showthread.php?t=1966777)

Reboot into Unity, then delete any extensions you may have in the two directories where they're stored:

(as root) /usr/share/gnome-shell/extensions
~/.local/share/gnome-shell/extensions

You don't need any terminal commands to do this. All extensions are self-contained javascripts.

Then reinstall what's available.

Just deleted my extensions, and am about to relog right now, let's hope it works.

> **jackson21 said:**
> Try a fresh install of ubuntu 12.04.
It will save you a lot of troubles, with outdated files 
an the system.
Consider the  short time time  of making a fresh install compared to the woes
of "flogging a dead horse" with outdated libraries!!!!

jackson from /Austria

I would try a fresh install, but I have a lot of stuff that isn't backed up. Granted the important stuff is on github or dropbox or my webservers, I just don't want to lose my filestructure, so the upgrade was the way to go.

UPDATE: After deleting my extensions, still the same problem. The shell itself doesn't seem to load [top bar, window border, etc], and I can't type in the password to unlock my keyring.

---

### Post by kohoutek1 on 2012-04-27
> UPDATE: After deleting my extensions, still the same problem. The shell  itself doesn't seem to load [top bar, window border, etc], and I can't  type in the password to unlock my keyring.

 Are you seeing any alerts such as "Ubuntu 12.04 has experienced an internal error?"

When you say "keyring," do you mean to login to the system at the login screen?

A fresh install might be the best route for you. That's what I'd do if I still couldn't resolve the problem.

What are you login options on the login screen?

Mine have "GNOME Panel", "GNOME", "GNOME Classic," GNOME Classic No effects, and "User Defined Session."

You might need to create a login profile that leads to GNOME.

---

### Post by |{urse on 2012-04-27
Since you're at the point of considering a fresh install try another DE, couldn't hurt.

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-lxde-desktop](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-lxde-desktop)

Hopefully that will give you a functioning desktop so you can continue to work on rectifying your gnome-shell issues.

---

### Post by yayramen on 2012-04-27
> **kohoutek1 said:**
> Are you seeing any alerts such as "Ubuntu 12.04 has experienced an internal error?"

When you say "keyring," do you mean to login to the system at the login screen?

A fresh install might be the best route for you. That's what I'd do if I still couldn't resolve the problem.

What are you login options on the login screen?

Mine have "GNOME Panel", "GNOME", "GNOME Classic," GNOME Classic No effects, and "User Defined Session."

You might need to create a login profile that leads to GNOME.

When I say 'keyring' I mean the prompt that comes up if you don't have it set to unlock the default gnome keyring automatically. "Please enter password to unlock keyring" or something.

And my options are
GNOME
GNOME Classic
GNOME Classic (No Effects) < currently using
Ubuntu
Ubuntu 2D
User Defined Session

---

### Post by yayramen on 2012-04-27
> **|{urse said:**
> Since you're at the point of considering a fresh install try another DE, couldn't hurt.

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-lxde-desktop](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-lxde-desktop)

Hopefully that will give you a functioning desktop so you can continue to work on rectifying your gnome-shell issues.

I'm using gnome-classic now. And although a little laggy, it seems to be doing just fine. That's another thing, things are laggy now. Gnome-Do, for example, is my alt+f2 hotkey, and it takes an extra second or so to pop up. Just drudging along. I'm not all that surprised, as my computer is circa 2008ish, but it was top of the line then, with a dual core 2.4ghz proc, and 4gb RAM, so I don't know what's going on. 

Oh wells. Maybe I'm stuck on gnome classic D:

Or, I could risk backing things up and restoring them later.

---

### Post by yayramen on 2012-04-27
I am just going to back up my stuff and re install 11.10.
I don't like how laggy my computer is with 12.04

---

### Post by LemursDontExist on 2012-04-27
> **yayramen said:**
> I am just going to back up my stuff and re install 11.10.
I don't like how laggy my computer is with 12.04

This would be a good time to make separate root and home partitions if you haven't already.  I did a fresh install yesterday, but I kept my home partition intact, and gnome-shell is working fine - not having to back up data saves a lot of time.  

Also, if you manage to break your machine somehow, if you have a separate home partition, the 'reinstall' option is almost totally painless.

---

### Post by yayramen on 2012-04-27
> **LemursDontExist said:**
> This would be a good time to make separate root and home partitions if you haven't already.  I did a fresh install yesterday, but I kept my home partition intact, and gnome-shell is working fine - not having to back up data saves a lot of time.  

Also, if you manage to break your machine somehow, if you have a separate home partition, the 'reinstall' option is almost totally painless.

I have no idea what you mean separating home and root partitions. I didn't plan on wiping when I get 11.10 downloaded, it should at least leave the file structure intact, is what I'm hoping. I can fix programs and dependencies.

---

### Post by LemursDontExist on 2012-04-27
At install time you can choose to split your hard drive into partitions for various purposes.  If you choose make a small (15-20GB) partition for root (/) and give the rest to /home then you can reinstall the OS will cleanly erasing what was there before without disturbing your data and settings which are all stored on /home.

This approach can save you a lot of time.  For instance, instead of doing upgrades every 6 months, I can just wipe the root partition clean and do a fresh install, and it takes no longer than an upgrade with far less risk of bugs.  As an added bonus, if you mess up your OS install, you can reinstall quickly without losing data or settings.  I really can't recommend this strongly enough!

---

### Post by yayramen on 2012-04-27
> **LemursDontExist said:**
> At install time you can choose to split your hard drive into partitions for various purposes.  If you choose make a small (15-20GB) partition for root (/) and give the rest to /home then you can reinstall the OS will cleanly erasing what was there before without disturbing your data and settings which are all stored on /home.

This approach can save you a lot of time.  For instance, instead of doing upgrades every 6 months, I can just wipe the root partition clean and do a fresh install, and it takes no longer than an upgrade with far less risk of bugs.  As an added bonus, if you mess up your OS install, you can reinstall quickly without losing data or settings.  I really can't recommend this strongly enough!

That sounds good enough for me! I am currently waiting for my Documents folder to sync with Ubuntu One. Once that's done, I think I'm going to do a fresh install, as all my important work is already on github, and my music is on my phone.

Ubuntu One is taking too long, switched to dropbox, same difference though.

---

### Post by johnnyhajjar on 2012-04-28
i upgraded and had this problem. then i did a fresh install and still have this problem. Unity 2d works as does gnome classic. Regular gnome and unity do not work and I get an internal error message in gnome. Screen either stays black or I only see the Desktop (no menus or anything). I think it might be graphics driver related, but I am not sure, Any ideas? I have the nvidia current version driver installed. My computer is a amd turion 64 x2 hp laptop. I had no problems running gmone 3 in 11.10.

---

### Post by yayramen on 2012-04-28
> **johnnyhajjar said:**
> i upgraded and had this problem. then i did a fresh install and still have this problem. Unity 2d works as does gnome classic. gnome and unity (regular( do not work and I get an internal error message in gnome. I think it might be graphics driver related, but U am not sure, Any ideas?

That sounds like a graphics driver to me. I'd boot into gnome classic and make sure everything's updated and try again. It's also fair to note that while I do have my gnome-shell back, I did it by wiping my computer and install 11.10 rather than 12.04. I unfortunately never figured out what went wrong, so I won't be able to help much.

---

### Post by kohoutek1 on 2012-04-29
> It's also fair to note that while I do have my gnome-shell back, I did it by wiping my computer and install 11.10 rather than 12.04. I unfortunately never figured out what went wrong, so I won't be able to help much.

Good to hear you got your shell back.

It would have been interesting to figure out what was conflicting in your previous installation.

I don't have the keyring issues, but then I don't make use of keyrings. I do have the screen lock enabled, but then I don't get a message that says "Please enter your password to unlock the keyring (or screen)." I only get a simple "Password:" window with an "Unlock" button. If you had keyring issues, you might try to see if others have reported similar bugs at launchpad.org.

It sounds like you might have had some extensions -- including possibly some framework items -- installed from 3.2 that were conflicting with those of 3.4. I also had some, and purging the extensions fixed it for me. There was one item I had to purge through synaptic, though: globalmenu-manager. That one was crashing my shell and it wasn't in my extension folders (globalmenu was, but not "-manager."). It was deprecated lib file left over from 3.2. 

In that case, then fresh install would have fixed it for you, and apparently did.

---

### Post by yayramen on 2012-04-29
> **kohoutek1 said:**
> Good to hear you got your shell back.

It would have been interesting to figure out what was conflicting in your previous installation.

I don't have the keyring issues, but then I don't make use of keyrings. I do have the screen lock enabled, but then I don't get a message that says "Please enter your password to unlock the keyring (or screen)." I only get a simple "Password:" window with an "Unlock" button. If you had keyring issues, you might try to see if others have reported similar bugs at launchpad.org.

It sounds like you might have had some extensions -- including possibly some framework items -- installed from 3.2 that were conflicting with those of 3.4. I also had some, and purging the extensions fixed it for me. There was one item I had to purge through synaptic, though: globalmenu-manager. That one was crashing my shell and it wasn't in my extension folders (globalmenu was, but not "-manager."). It was deprecated lib file left over from 3.2. 

In that case, then fresh install would have fixed it for you, and apparently did.

Yeah, I had tried that. I had a small number.
Disable hotspot, classic systray, remove accessibility button, and the alt-tab window one [that switches through windows rather than programs]

I removed all those, and still nothing, but maybe I forgot one.

And it wasn't keyring issues, it was typing issues. I couldn't TYPE in the keyring box. It was simple password, and I was able to copypaste the letters from the prompt to get it (xD) and it unlocked just fine. But the shell itself never loaded. I only had the desktop.

---

### Post by gregwilkins on 2012-07-13
I just upgraded to 12.04 and gnome shell extensions have all stopped working.   I have removed all the installed ones from both directories and logged in again, but when I go to extensions.gnome.org there are no extensions listed at all? so nothing to install.

<rant>
I really think that Ubuntu is losing it. Every release is worse than the previous one.  It used to be that I looked forward to updates to see what great new things were available.  Now it is something I loath as it always breaks vital things.  In this case I lost wifi and my desktop on a very common laptop - how can they seriously call this a LTS version?
</rant>

---

### Post by gregwilkins on 2012-07-13
Some further information!  If I create a new user account on my system, then gnome extensions work fine!  So it is something in my account??
Any ideas where to look for gnome-shell settings that might be old?

---

### Post by yayramen on 2012-07-13
I had never even though of making a new account. But, no it's odd. the two places listed are the only places I had ever found. I ended up just staying with 11.10 as it was MUCH MUCH snappier. Sorry I can't be of any more help, but I never did figure it out D:

---

### Post by Muzafsh on 2012-09-22
not just an upgrade to 12.04 kills gnome-shell ... but even otherwise a clean install that i did ... is facing gnome failures ... my failure is more towards the gnome-shell-extensions ... i have been using ubuntu for the last 4-5 years ... and i hadn't explored much on desktop applications (unity, gnome, etc) ... now that i upgraded to 12.04 thru a clean install ... i was just aw-struck at unity being integrated into 12.04 ... i really liked the window key(super L) key and the 'left+alt' function of unity ... and somehow i got myself to install gnome3 on my 12.04 ... and i was aw-struck twice on a single day ... it was better and far superior than unity ... i was just sucked into this new world of Gnome 3 and the way the shell-extensions brought more value to the whole experience ... 

but alas my experience was short lived ... after a couple of routine OS updates the shell-extensions tanked and i am left with the Gnome 3 Default extensions ... with no way to install or revive the so many great extensions i had set up ...

ITS SUCH A LET DOWN !!! ... a routine upgrade too can mess the whole Gnome 3 experience ...

If anybody is interested in helping ... just drop in a word ... and i'll provide readings out of my system to help diagnose the issue i faced ...

---

### Post by Seinfeld on 2013-05-22
Hi ..

Thanks for this valuable info. Now, I want to upgrade to 12.04 from 10.04. Any one could tell me please, how can I keep my gnome desktop settings such as, panels, icons, wallpaper, gconf settings etc.. ??
I did upgrade 12.04 on another machine and after installing gnome-shell and gnome-session-fallback, it took me several hours to arrange my desktop the same it was from scratch.
Also, I would like to use my 10.04 gdm screen too if possible. Is there a folder(s) that stores my old desktop settings so I can back it up and overwrite the new 12.04 one with it ??

Thanks so much

---

