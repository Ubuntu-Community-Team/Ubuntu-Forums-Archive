---
title: "New GDM is uploaded"
date: 2009-07-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by plun on 2009-07-02
> gdm (2.26.1-0ubuntu1) karmic; urgency=low

  * Upload the new gdm codebase to karmic, there is several known issues but
    the new version need testing:
    - there is no graphical configure tool yet
    - gdm will not work correctly after upgrade until restart (restarting on
      upgrade is not possible since it would close running xsession)
    - the fast user switch applet ubuntu changes and the guest session
      have not been updated yet

[https://lists.ubuntu.com/archives/karmic-changes/2009-July/003527.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/003527.html)


Lets find these bugs.....;)

---

### Post by wayne_cat on 2009-07-02
does is still use the settings from:

/etc/gdm/gdm.conf

---

### Post by nhasian on 2009-07-02
i'd like to buy the gdm is waiting on something.  update manager tells me its a partial upgrade.

---

### Post by jppr on 2009-07-02
gdm is not updated yet, but just became a new kernel

---

### Post by plun on 2009-07-02
> **jppr said:**
> gdm is not updated yet, but just became a new kernel

Well, I am running the new GDM.... strange login...):P

---

### Post by wayne_cat on 2009-07-02
Gnome starts fully automatically .. I don't even have to enter my username/password :-?

---

### Post by nhasian on 2009-07-02
you should probably start a new thread.

according to:

```
apt-cache policy nvidia-glx-180
```

the latest version in the repos is 185.18.14-0ubuntu2.

> **tad1073 said:**
> I keep getting build failure w/ 2.6.31.1 + nvidia 190.09

---

### Post by Vanishing on 2009-07-02
> **nhasian said:**
> i'd like to buy the gdm is waiting on something.  update manager tells me its a partial upgrade.

+1 confirm on partial upgrade...it will delete fast-user-switch and ubuntu-desktop...

---

### Post by graaant on 2009-07-02
I've been using the new GDM for a while from the ubuntu-desktop PPA.
Problem is that it seems to load twice at boot, I log in, blank screen then GDM again and log in.
After that I recieve this error from Metacity...
```
"These windows do not support "save current setup" and will have to be restarted manually next time you log in." 
Class - Login Window
Window - GDM Simple Greeter
```Anyone got any ideas?

---

### Post by buzzmandt on 2009-07-02
also partial

---

### Post by wayne_cat on 2009-07-02
> **graaant said:**
> I've been using the new GDM for a while from the ubuntu-desktop PPA.
Problem is that it seems to load twice at boot, I log in, blank screen then GDM again and log in.
After that I recieve this error from Metacity...
```
"These windows do not support "save current setup" and will have to be restarted manually next time you log in." 
Class - Login Window
Window - GDM Simple Greeter
```Anyone got any ideas?

 GDM did not start after the update so I removed (apt-get remove --purge) and reinstalled it. No I get the GDM login screen ... but I also get this message (Anmeldefenster = the german word for "Login Window").

[[IMG]http://ubuntu-pics.de/thumb/17662/metacity_063OBA.png[/IMG]]("http://ubuntu-pics.de/bild/17662/metacity_063OBA.png")

---

### Post by graaant on 2009-07-02
> **wayne_cat said:**
> GDM did not start after the update so I removed (apt-get remove --purge) and reinstalled it. No I get the GDM login screen ... but I also get this message (Anmeldefenster = the german word for "Login Window").

[[IMG]http://ubuntu-pics.de/thumb/17662/metacity_063OBA.png[/IMG]]("http://ubuntu-pics.de/bild/17662/metacity_063OBA.png")

Yeah that's exactly the error message I get.
I've no idea where the configs for this GDM are either :S

---

### Post by wayne_cat on 2009-07-02
> **graaant said:**
> Yeah that's exactly the error message I get.
I've no idea where the configs for this GDM are either :S

There are settings in /etc/gdm and you can change things with gconf-editor. Maybe a missing/false option.

[[IMG]http://ubuntu-pics.de/thumb/17664/simple_greeter_tKN60O.png[/IMG]]("http://ubuntu-pics.de/bild/17664/simple_greeter_tKN60O.png")

---

### Post by graaant on 2009-07-02
> **wayne_cat said:**
> There are settings in /etc/gdm and you can change things with gconf-editor. Maybe a missing/false option.

[[IMG]http://ubuntu-pics.de/thumb/17664/simple_greeter_tKN60O.png[/IMG]]("http://ubuntu-pics.de/bild/17664/simple_greeter_tKN60O.png")

I'm not seeing anything in there that looks out of place. Your screenshot is the same as my screen.

---

### Post by scradock on 2009-07-02
For me, the update manager marked gdm as not installable, so I accepted everything else, restarted and then switched to synaptic to see what gdm needed. It said it would have to remove the fast-user-switcher applet (lots of fast users on my machine, I'm sure....) and ubuntu-desktop. 

Well, I saw the note in the changelog that f-u-s would not be updated to suit, so that was OK, and Ubuntu-desktop is a catch-all to bring in other things, so it can go too. So I accepted the upgrade for gdm, gdm-themes and a couple of other packages.

Part way through the install process the screen went black, and I had no keyboard or trackpad responses (no effect with Ctl-Alt-F1, Ctl-Alt-BkSp, Ctl-Alt-Del, or even Alt-SysRq-REISUB).

So I powered off and tried rebooting. No log-in window, long delay, but eventually desktop emerges from the darkness, but no applets, no Trash, no Application bars in the lower panel, etc. Makes switching off kind of painful.

But it does start.

Now what were those bugs we were looking out for? It seems really hard to sort out what to report as a bug when basic functions aren't even there yet. Add this to the chaos of a new kernel (2.6.31-1) that breaks X (if you have an Intel, or Nvidia, or ATI graphics card, so far as I've seen.....).

We are indeed testing in interesting times, as the old Chinese curse puts it.

---

### Post by autocrosser on 2009-07-02
Only reason it's "uninstallable" is that it removes fast-user-switch applet--if your not using it--just use Synaptic & accept the upgrade.

Sorry--I didn't read all thru your post--you might try reinstalling GDM....

---

### Post by wayne_cat on 2009-07-02
scradock,

have a look at the gdm log files in:

/var/log/gdm

Maybe you will find something that will help you.

Well .. the new kernels ... I'm back to 2.6.30-9-generic ... the last version that make no trouble on my notebook.

---

### Post by DougieFresh4U on 2009-07-02
So I have read through the whole thread. 
My question is, through Synaptic upgrade, it wants to remove 'ubuntu-desktop AND gnome-desktop environment, & gnome
I always thought that I needed one of those desktops in order to have functioning desktop. :confused::confused:

---

### Post by kingborel on 2009-07-02
GDM installed for me, but I get the 'Save current setup' error and no theme support yet

---

### Post by wayne_cat on 2009-07-02
> **DougieFresh4U said:**
> So I have read through the whole thread. 
My question is, through Synaptic upgrade, it wants to remove 'ubuntu-desktop AND gnome-desktop environment, & gnome
I always thought that I needed one of those desktops in order to have functioning desktop. :confused::confused:

wait for a day or two ... you are the first in this thread with this problem.

---

### Post by Yes_It's_Me on 2009-07-02
I get the same login error as everyone else here, but it does (mostly) work for me. Obviously nvidia is still broken and i can't be stuffed patching it because i am lazy (they will fix that soon anyway i guess). It smoothly fades in and stuff. But after typing in the password it just cuts to the desktop with the error, no smooth sexy fade out yet.

But it's something.

---

### Post by hanzomon4 on 2009-07-02
What is this new gdm?

---

### Post by wayne_cat on 2009-07-02
interesting question ... that I can't answer. I can just show you what it looks like:

[[IMG]http://ubuntu-pics.de/thumb/17667/gdm_screenshot_gbKn73.png[/IMG]]("http://ubuntu-pics.de/bild/17667/gdm_screenshot_gbKn73.png")

---

### Post by graaant on 2009-07-02
I believe that's GDM 2.26
GNOME moved to that a while ago, but Ubuntu kept 2.24 because new GDM still has no graphical config.
Correct me if I'm wrong :)

---

### Post by wayne_cat on 2009-07-02
> **graaant said:**
> I believe that's GDM 2.26
GNOME moved to that a while ago, but Ubuntu kept 2.24 because new GDM still has no graphical config.
Correct me if I'm wrong :)


[http://www.mail-archive.com/karmic-changes@lists.ubuntu.com/msg03203.html](http://www.mail-archive.com/karmic-changes@lists.ubuntu.com/msg03203.html)


well .. the new gdm removed the configuration option from the gnome menu ...  no need to correct you ;)

---

### Post by scradock on 2009-07-02
> **graaant said:**
> I believe that's GDM 2.26
GNOME moved to that a while ago, but Ubuntu kept 2.24 because new GDM still has no graphical config.
Correct me if I'm wrong :)
AFAIK Ubuntu has been hanging in with 2.20, not even 2.24. No surprises if there are surprises with a jump like that all in one go. But I will try re-installing - thanks for the helpful suggestion. 

I would probably have done it anyway, after the install blak-screened halfway through, except that it amazingly worked, at least when I typed startx after being dropped to a terminal prompt.

By the way, I checked /etc/X11/default-display-manager, which used to read \:

/usr/sbin/gdm

and found that it contained:

als instantly

instead - same number of characters (14).

Seemed to help a bit when i switched back to the old version, but still no panelsp contents....

---

### Post by scradock on 2009-07-03
Yes, reinstalling gdm helped a lot - I got my panel applets back, all but fast-user-switcher, of course. Still no way to restart, suspend or hibernate, or even Shutdown! They are all supposed to be in f-u-s, and don't appear anywhere else as far as I can see. The System menu only has Log-out, which actually doesn't - it ends the Xsession, and leaves me logged in at console level. All very weird.

---

### Post by graaant on 2009-07-03
I've got Lock Screen and Quit options and can Quit to GDM then restart or shutdown from there.
Not great, but it works.

---

### Post by hanzomon4 on 2009-07-03
Ok I was thinking that it was the much talked about login experience/ face browser thing. This is cool though, just not what I've been waiting for since... feisty?

---

### Post by autocrosser on 2009-07-03
> **scradock said:**
> Yes, reinstalling gdm helped a lot - I got my panel applets back, all but fast-user-switcher, of course. Still no way to restart, suspend or hibernate, or even Shutdown! They are all supposed to be in f-u-s, and don't appear anywhere else as far as I can see. The System menu only has Log-out, which actually doesn't - it ends the Xsession, and leaves me logged in at console level. All very weird.

Look in panel applets--I do not use f-u-s & just installed separate applets for the functions i needed--If you don't see what you need--you should also look in Synaptic--

---

### Post by Joe_Bishop on 2009-07-03
Like it, looks much better than ugly blacky gdm from jaunty.

---

### Post by Nossile on 2009-07-03
> **wayne_cat said:**
> GDM did not start after the update so I removed (apt-get remove --purge) and reinstalled it. No I get the GDM login screen ... but I also get this message (Anmeldefenster = the german word for "Login Window").

[[IMG]http://ubuntu-pics.de/thumb/17662/metacity_063OBA.png[/IMG]]("http://ubuntu-pics.de/bild/17662/metacity_063OBA.png")

Excluding the file "Metacity" of /usr/share/gdm/autostart/LoginWindow, the message is not displayed anymore.

but it can "kill kittens" ;)

---

### Post by graaant on 2009-07-03
> **Nossile said:**
> Excluding the file "Metacity" of /usr/share/gdm/autostart/LoginWindow, the message is not displayed anymore.

but it can "kill kittens" ;)

Can you explain this a little better?

---

### Post by Nossile on 2009-07-03
> **graaant said:**
> Can you explain this a little better?

See the image.

---

### Post by graaant on 2009-07-03
> **Nossile said:**
> See the image.

Ah I see, thanks that helped!

Now I've just got to stop it from loading twice.

---

### Post by alphacrucis2 on 2009-07-03
> **graaant said:**
> I've got Lock Screen and Quit options and can Quit to GDM then restart or shutdown from there.
Not great, but it works.

I just did 

```
sudo shutdown -h now
```

or 

```
sudo shutdown -r now
```

Haven't had to use those for a while:p

---

### Post by SKLP on 2009-07-03
> **wayne_cat said:**
> interesting question ... that I can't answer. I can just show you what it looks like:

[[IMG]http://ubuntu-pics.de/thumb/17667/gdm_screenshot_gbKn73.png[/IMG]]("http://ubuntu-pics.de/bild/17667/gdm_screenshot_gbKn73.png")

YEEEES!!!
Finally we can have a GDM which looks like Fedoras ;-)
IMO it was fedoras biggest advantage when I tried it a while back

---

### Post by Frantique on 2009-07-03
Hello all,
I am getting errors on Gdm start: 

Unable to load file '/etc/gdm/gdm.conf-custom': No such file
Unable to read schemas file: Cannot open '/etc/gdm/gdm.schemas': No such file
Unable to parse shemas
Unable to initialize settings

I have tried to purge and reinstall gdm, but it does not helps. Before the last upgrade everything was just fine. Any ideas?

---

### Post by davideotape on 2009-07-03
I'm liking the new GDM, and the username upgrade on the panel

---

### Post by zika on 2009-07-03
After GDM upgrade (which I like and which went OK since I went "down" to CLI (log-out from previous gdm) and then upgraded) I cannot write .iso to CD with Brasero. I can read CD OK.

---

### Post by whoop on 2009-07-03
Shutting down the system require some extra steps now. I reckon this is temporary.

---

### Post by tjeremiah on 2009-07-03
I like the fast user switch but most likely ill be the only one on this notebook. Its cool, just that I want my suspend,hibernate,shutdown options back in the user menu on the panel.

---

### Post by wayne_cat on 2009-07-03
> **Frantique said:**
> Hello all,
I am getting errors on Gdm start: 

Unable to load file '/etc/gdm/gdm.conf-custom': No such file
Unable to read schemas file: Cannot open '/etc/gdm/gdm.schemas': No such file
Unable to parse shemas
Unable to initialize settings

I have tried to purge and reinstall gdm, but it does not helps. Before the last upgrade everything was just fine. Any ideas?

gdm.conf-custom is also missing on my system ... but the file gdm.schemas is there.
See the attached file ... I had to rename it to gdm.schema.txt to upload it.

```
root@macbook:~# ls -la /etc/gdm/
total 48
drwxr-xr-x   6 root root  4096 Jul  3 00:05 .
drwxr-xr-x 163 root root 12288 Jul  3 14:42 ..
drwxr-xr-x   2 root root  4096 Jul  2 23:58 Init
drwxr-xr-x   2 root root  4096 Jul  2 23:58 PostLogin
drwxr-xr-x   2 root root  4096 Jul  2 23:58 PostSession
drwxr-xr-x   2 root root  4096 Jul  2 23:58 PreSession
-rwxr-xr-x   1 root root  6259 Jul  2 17:02 Xsession
-rw-r--r--   1 root root   105 Jul  3 00:05 custom.conf
-rw-r--r--   1 root root  2555 Jul  2 17:02 gdm.schemas
root@macbook:~# 
```

---

### Post by zika on 2009-07-03
> **tjeremiah said:**
> I like the fast user switch but most likely ill be the only one on this notebook. Its cool, just that I want my suspend,hibernate,shutdown options back in the user menu on the panel.If I understood You right, You can get to them with Ctrl-(L)Alt-Del ... :)

---

### Post by tad1073 on 2009-07-03
The new GDM isn't playing nice, have to login twice and it seems to tied to metacity

---

### Post by pferraro on 2009-07-03
> **tad1073 said:**
> The new GDM isn't playing nice, have to login twice and it seems to tied to metacity

You can change it to use compiz by toggling the following gconf property:
/apps/gdm/simple-greeter/wm_use_compiz

---

### Post by b3n87 on 2009-07-03
Can someone post a screen shot of the new GDM please?

---

### Post by meeples on 2009-07-03
the new gdm is barfing up my laprop upgrade to karmic.

i went away and left it to upgrade, came back it was at the login screen, i assume it had finished so i login.

go to synaptic,

"dpkg was interrupted" blah blah blah

so i go to terminal put in the command synaptic tells me...
```
sudo dpkg --configure -a
```

and halfway through i get logged out again.

so i have half an installation apparently.

please say theres a way to get by this haha

---

### Post by DougieFresh4U on 2009-07-03
> **b3n87 said:**
> Can someone post a screen shot of the new GDM please?

See post #25 of this thread  :idea:

---

### Post by tjeremiah on 2009-07-03
> **zika said:**
> If I understood You right, You can get to them with Ctrl-(L)Alt-Del ... :)

thanks, its a good hand stretcher exercise. Who maps these keys?

---

### Post by davideotape on 2009-07-03
> **tjeremiah said:**
> thanks, its a good hand stretcher exercise. Who maps these keys?

I presume those keys were taken from windows where they bring up a general task manager screen.

---

### Post by morryis on 2009-07-03
After upgrading to the new GDM, my Gnome keyboard-layout is always set to "USA" instead of "Germany" after login. I have to select "Reset to Defaults" in gnome-keyboard-properties every time i restart Ubuntu to set the german layout.

---

### Post by tjeremiah on 2009-07-03
> **davideotape said:**
> I presume those keys were taken from windows where they bring up a general task manager screen.

oh, didnt know that :(

---

### Post by chrisccoulson on 2009-07-03
> **morryis said:**
> After upgrading to the new GDM, my Gnome keyboard-layout is always set to "USA" instead of "Germany" after login. I have to select "Reset to Defaults" in gnome-keyboard-properties every time i restart Ubuntu to set the german layout.

This is because the new GDM is setting the environment variable GDM_KEYBOARD_LAYOUT to "us" by default when no layout is selected in the greeter (there is no layout chooser at the log in screen anyway). See [https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/395103]("https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/395103")

---

### Post by plun on 2009-07-03
> **chrisccoulson said:**
> This is because the new GDM is setting the environment variable GDM_KEYBOARD_LAYOUT to "us" by default when no layout is selected in the greeter (there is no layout chooser at the log in screen anyway). See [https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/395103]("https://bugs.edge.launchpad.net/ubuntu/+source/gdm/+bug/395103")

Its the same with a swedisk keyboard....  å,ä,ö...;)

Update is coming:

> gdm (2.26.1-0ubuntu2) karmic; urgency=low

  * debian/control: Add Vcs-Bzr, package imported into bzr.
  * Add 02_dont_force_us_keyboard.patch: Don't force GDM_KEYBOARD_LAYOUT=us if
    gdm does not have an explicit setting (which it currently doesn't, since
    there is not even an interface for changing the keyboard layout). Instead,
    let the GNOME session default to the very same system default as gdm
    itself. (LP: #395103)


---

### Post by chrisccoulson on 2009-07-03
> **plun said:**
> Its the same with a swedisk keyboard....  å,ä,ö...;)

Update is coming:

Yep;)

---

### Post by ranch hand on 2009-07-03
Someone was saying they thought this was Gnome 2.6.  It is Gnome 2.7.3.

It is a little rough around the edges but seems to work fine for what it is set up to do currently.

We will be seeing a lot of updates for this bugger I think.

---

### Post by tjeremiah on 2009-07-03
I dont know if this is random, but I was about to type 2006, I managed to hit 2,0 and all of a sudden, my screen turns black and im booted back to the gdm.

---

### Post by tjeremiah on 2009-07-03
Ok, what just happed? I just did an update again, just now. While updating, im not sure if it finished, once again I was greeted with a black screen out of nowhere. I had to reboot the system and now im greeted with a screwed up panel and different window borders. 

Pictures are from before and after.

---

### Post by MacUntu on 2009-07-03
Screen went black during latest upgrade (session restarted) but my panels are ok.

---

### Post by tad1073 on 2009-07-03
New gdm sucks really hard. With the new update, still have to login twice, changes widow border to metacity, gconf>apps>gdm>simple-greeter>wm_use_compiz doesnt
 work.

bug report filed: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395302](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395302)

---

### Post by MacUntu on 2009-07-03
How can something that obviously isn't fully integrated "suck really hard"? If you don't wanna experience such surprises stay away from development versions. :P

---

### Post by tjeremiah on 2009-07-03
> **MacUntu said:**
> How can something that obviously isn't fully integrated "suck really hard"? If you don't wanna experience such surprises stay away from development versions. :P

its more fun.:p

---

### Post by tad1073 on 2009-07-03
> **MacUntu said:**
> How can something that obviously isn't fully integrated "suck really hard"? If you don't wanna experience such surprises stay away from development versions. :P

Because obviously the developers didn't test their product before pushing it out, but I guess thats what we are for.

---

### Post by autocrosser on 2009-07-03
You must remember that it is another "work-in-progress" from Gnome--when things are just released "into the wild", they normally do not work the way one wishes them to--If you don't like what you see--GET INVOLVED & do bug reports/get on the mailing list/DO SOMETHING to be constructive.

---

### Post by tad1073 on 2009-07-03
bug reported in this post

[http://ubuntuforums.org/showpost.php?p=7557415&postcount=61](http://ubuntuforums.org/showpost.php?p=7557415&postcount=61)

---

### Post by steeleyuk on 2009-07-03
The latest versions of GDM has been in Fedora for a while, so its been tested to some extent. Its just the Ubuntu version which isn't tested, hence the alpha versions...

---

### Post by autocrosser on 2009-07-03
Yes--I have seen it--tried both Fedora 10 & 11.

I just wish that more constructive discussion than "this sucks" were to be used..No slights intended, but I find that kind of talk offensive.

---

### Post by scradock on 2009-07-03
> **autocrosser said:**
> Yes--I have seen it--tried both Fedora 10 & 11.

I just wish that more constructive discussion than "this sucks" were to be used..No slights intended, but I find that kind of talk offensive.
Well, let's try, shall we? My experience suggests, strongly, and this is confirmed by reports from other people, that the "new" GDM in Ubuntu simply doesn't do what it is advertised as doing. Quote from the Description field:

"gdm provides the equivalent of a "login:" prompt for X displays- it
pops up a login window and starts an X session."

At the moment it doesn't bring up a login prompt at all, for me; it fails to bring up a working X-session and leaves me to login at a command-line prompt instead. This is after the re-install I did yesterday after the semi-successful first upgrade. I have seen no trace of any "new" login window.....And Yes, I have stopped trying to use the 2.6.31-1 kernel while I try to sort out GDM.

Added to the fact that it has made fast-user-switcher un-usable, and left many people without a reasonable way to log-off/shutdown, it does seem to me that it is not entirely unfair to say that it does not at present perform well enough even to be used for bug-testing.

---

### Post by steeleyuk on 2009-07-03
I'm finding it hard to sympathise when you're running Alpha 2. I could understand if you were running a stable release, possibly even a beta, but not an alpha. These things are to be expected.

If the bug(s) have been filed, then I'm pretty sure there will be an update this weekend, maybe Monday at the latest. Implementing something like GDM 2.26 is generally always going to cause breakage because its a large shift from the existing version.

---

### Post by autocrosser on 2009-07-03
Agreed--I am having problems as everyone else is--I get with it & get on the mailing list & do bug reports-- sign on to this one: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395313](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395313)

And i have a submit in on the dev-discuss-list....as soon as I get some info back, I'll post it.

My posting:> Greetings...

There has been several problems with the new GDM upload to Karmic--most  problematic is that during the update the xsession will close, causing  problems ranging from mild to very severe...Bug report:  [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395313](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395313)  & forum  discussion: [http://ubuntuforums.org/showthread.php?t=1202843](http://ubuntuforums.org/showthread.php?t=1202843)

Several people have had severe problems with partial upgrade leaving  them with text-only login & partial functionality.

Also, there seems to be no real way to change settings with the new GDM.  Could someone clarify the roadmap?

Thank you

Dean Loros
autocrosser at ubuntuforums.org

---

### Post by scradock on 2009-07-03
Thanks, autocrosser - that sounds like a very helpful beginning! Glad someone around here knows how to tackle the problem at the right level.

Just out of interest, I tried removing gdm completely - it was marked as autoremovable anyway. The exact same sequence occurs on start-up - clearly the new gdm is not being used at all on my machine. 

I did the removal at command-line - sudo apt-get remove gdm , then checked that it was marked as Not Installed in Synaptic. Then I tried re-insatlling in the same way, just in case it would install properly if there wasn't an active X-session. But still exactly the same behavior - boots to command line only, then startx gets the GNOME desktop going with its panels.

Ahah! without the new gdm I can have fast-user-switcher back again!! 

[Edit] Oh no I can't - it needs gdm (presumably 2.24, not 2.26....)

---

### Post by Arlanthir on 2009-07-03
Is this new GDM supposed to give us flickerfree transition from GDM to desktop, just a nice fade and etc?

---

### Post by expensivelesbian on 2009-07-03
I'm likewise having issues. If raising a ticket isn't too bad, I'll try and do so.

However, what I've noticed is that another account on my machine can login. I can't. The only difference I can see currently is that I'm using 'blood and stone' (grey thing, looks like a minimalist Aqua theme) theme, whereas the other user isn't using any themes other than default. Are themes breaking things?

---

### Post by autocrosser on 2009-07-03
At this stage anything is possible--try going back to a simple theme to see...as for bug reports--there are several just today--make sure you have a Launchpad account & bug check GDM...browse the reports & sign-on to the one that covers your problem...

I'll most likely have developer answers within the next couple of hours--my posting showed up on the list about 20min ago....

---

### Post by autocrosser on 2009-07-03
> **Arlanthir said:**
> Is this new GDM supposed to give us flickerfree transition from GDM to desktop, just a nice fade and etc?

Yes & faster desktop load is part of the plan also....keep one's fingers crossed that all happens...what with the grub2 change also I can say that we "live in interesting times" :p

Just remember---"breakage makes us better testers!!!!!"

---

### Post by Eclipse. on 2009-07-03
Well I totally borked the thing, the fact that my gdm.conf was tweaked a bit probally didnt help.;)

GDM fails to load completely with me, I get a message about the greeter application failed to load, clicking ok just loops the sequence.

I can get my desktop to load using startx but it just freezes straight away, I'm going reset my gdm.conf back to generic state then do some messing around.

Btw autocrosser, you got a response from Alexander Sack.

---

### Post by autocrosser on 2009-07-03
First reply & my return posting:> On 07/03/2009 03:56 PM, Alexander Sack wrote:[INDENT]   On Fri, Jul 03, 2009 at 03:35:10PM -0700, Dean Loros wrote:[INDENT]  Greetings...

There has been several problems with the new GDM upload to Karmic--most 
problematic is that during the update the xsession will close, causing 
problems ranging from mild to very severe...Bug report: 
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395313](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395313) & forum 
discussion: [http://ubuntuforums.org/showthread.php?t=1202843](http://ubuntuforums.org/showthread.php?t=1202843)
[/INDENT]For me gdm didnt really log out. Rather it triggered the "user
switch" screen and i was able to resume my running session by after
username/password.

 - Alexander


[/INDENT]Thank you for the respond Alexander....Any ideas 'bout some of the  problems the testing group has been having?

My experience with the second update was similar to a crash--I had  update manager in the background & was typing a post to the  forums---so I would guess that the keystrokes "confused" the  update...all came back after the reboot, but someone else in the testing  group has totally lost GDM...if you have the time, you might drop in to  the forum thread & read the last several pages.....


Cheers!!!!

Dean
Autocrosser

---

### Post by tad1073 on 2009-07-03
How do I go about getting the old gdm back?

---

### Post by autocrosser on 2009-07-03
I would say--go back to Jaunty---Sorry, it looks like 2.26 is here---I have raised a bit of dust on Dev-list:
From Max Bowsher---> Alexander Sack wrote:[INDENT]> On Fri, Jul 03, 2009 at 03:35:10PM -0700, Dean Loros wrote:[INDENT]>>   Greetings...
>>
>> There has been several problems with the new GDM upload to Karmic--most 
>> problematic is that during the update the xsession will close, causing 
>> problems ranging from mild to very severe...Bug report: 
>> [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395313](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395313) & forum 
>> discussion: [http://ubuntuforums.org/showthread.php?t=1202843](http://ubuntuforums.org/showthread.php?t=1202843)
[/INDENT]> 
> For me gdm didnt really log out. Rather it triggered the "user
> switch" screen and i was able to resume my running session by after
> username/password.
[/INDENT]Alexander,

I experienced what you describe above when upgrading from old gdm to new
gdm, ***but*** when I later upgraded from one package version of new gdm to
a slightly newer one, it killed my session outright.


Either way, even triggering the "user switch" screen in the middle of a
jaunty->karmic upgrade would be very bad user experience.

Max.





Good show Max-----

---

### Post by tjeremiah on 2009-07-04
things are a lot better now.

---

### Post by autocrosser on 2009-07-04
OK--I fixed my b0rked GDM...but its a way that takes a bit of work....I pulled the .deb for the current GDM (/var/cache/apt/archives)--opened data.tar with File Roller to my desktop & hand-pasted the contents of /usr & /etc (/etc/gdm, /usr/share/gdm & /gconf and /usr/lib/gdm) to the same places in my system--then logged out/in.....got the "new" look back (had a Fedora-like look before) & it seems to work normal again---at least as normal as the new GDM works ;)

---

### Post by zika on 2009-07-04
Upgrade of gdm should be done from CLI. Log-out from gdm and login-in in CLI. Then upgrade. Even though last upgrade (for me, taking out the fact that black screen scared the **** out of me) went without a glitch. I must say that log-out and log-in again (when having AutomaticLoginEnable=true) is lightening fast... :)

---

### Post by autocrosser on 2009-07-04
Yes--that way would be best in light of what has been happening---but this is a "glitch" that should not have happened in the first place---people were not expecting a update that has not needed any abnormal work before to b0rk systems so badly......I have posted in both bug report & dev-list as to that fact.

---

### Post by zika on 2009-07-04
> **autocrosser said:**
> Yes--that way would be best in light of what has been happening---but this is a "glitch" that should not have happened in the first place---people were not expecting a update that has not needed any abnormal work before to b0rk systems so badly......I have posted in both bug report & dev-list as to that fact.Exactly what I meant to say, maybe I was not clear enough. But it in testing period we should be prepared for all situatuions ... ;) So I disabled AutoLogin in order to be able to get to CLI fast enough ... :) And no background upgrades since Jaunty testing ... :)

---

### Post by taavikko on 2009-07-04
The X-session seems to be running in tty3 nowadays...

---

### Post by zika on 2009-07-04
> **taavikko said:**
> The X-session seems to be running in tty3 nowadays...?

---

### Post by autocrosser on 2009-07-04
> **zika said:**
> Exactly what I meant to say, maybe I was not clear enough. But it in testing period we should be prepared for all situatuions ... ;) So I disabled AutoLogin in order to be able to get to CLI fast enough ... :) And no background upgrades since Jaunty testing ... :)

Ya--I was doing a background upgrade the second time :( ---sloppy I know, but I was posting to this thread when it happened :rolleyes: 

I normally watch updates very closely--shows what happens when you let your guard down:mad::p):P

---

### Post by tad1073 on 2009-07-04
> **autocrosser said:**
> I would say--go back to Jaunty---Sorry, it looks like 2.26 is here---I have raised a bit of dust on Dev-list:

If I could get wireless to work under 9.04 I probably would.

---

### Post by autocrosser on 2009-07-04
Well---I would say that the devs now "know' about the bit of trouble this has caused....
I just hope that things are worked on quickly.........So I would just hang in there--you know that Alphas can be a rough ride some times....

---

### Post by taavikko on 2009-07-04
> **zika said:**
> ?

GDM starts an X-session on first available tty.
tty[1-6] is reserved for virtual consoles, and the 7 is the first free one

Whups.... My bad, just did a check, Seems i've disabled active consoles [3-6] hence the X starts on tty3.
((This is done by me so automatically that I keeps forgetting thiz))

---

### Post by zika on 2009-07-04
> **taavikko said:**
> GDM starts an X-session on first available tty.
tty[1-6] is reserved for virtual consoles, and the 7 is the first free one

Whups.... My bad, just did a check, Seems i've disabled active consoles [3-6] hence the X starts on tty3.
((This is done by me so automatically that I keeps forgetting thiz))Do You also do it by editing /etc/init.d/tty3-tty6 or is there a faster (or better) way ... ?

---

### Post by tad1073 on 2009-07-04
> **autocrosser said:**
> Well---I would say that the devs now "know' about the bit of trouble this has caused....
I just hope that things are worked on quickly.........So I would just hang in there--you know that Alphas can be a rough ride some times....

I just tried your way and am getting the same results.

What is the command to install a .deb via terminal?

Alpha 2 has been a smooth ride up until now.

---

### Post by taavikko on 2009-07-04
> **zika said:**
> Do You also do it by editing /etc/init.d/tty3-tty6 or is there a faster (or better) way ... ?

AFAIK that editing /etc/default/console-setup isn't sufficient and need also to edit ../init.d/tty{3,4,5,6} by hand to prevent them from respawning.

enough from offtopic :)

This talk on "black screen" don't think it's due to the new GDM as my KDE is doing this too.
Difference is that the gdm respawns but KDE session is terminated. So would but my pointing two fingers in the X

---

### Post by taavikko on 2009-07-04
> **tad1073 said:**
> 
What is the command to install a .deb via terminal?


"sudo dpkg -i packagename"

---

### Post by ranch hand on 2009-07-04
I actually have 3 versions of 9.10 on this box.  A1-32 and A2-64 both on 2 partitions and A2-64 on one partition just to play with grub.

The 32 version is run with 2 of my cpus off so that I am running 32.

All three were updated to 2.6.31-1 and the new GDM today.

I did have some wierd things happen.  The 32 version rebooted when I updated and I wasn't sure it was done but everything was fine.  I have had all 3 versions go to black and require me to relog but this was not to much hassle because every thing came back up the way I had it before the log in.  It was just like going from a "guest" session back to my session.

Considering the lack of problems that have come up in 9.10 I would say that it is a pretty stable little bugger.  We have 2 fairly major changes, Grub2 and this GDM, and while niether are right on, right now, I think that, overall, Karmic is coming along very nicely.  If the GDM improves as fast as Grub2 to is this problem should go away very soon.

I do not like the style lf shut down that I am stuck with right now.  It works but has too many clicks.  I put the shut down applet on my panel so that I could shut down or reboot faster.

This may work for folks that want to Hibernate there box.  I don't know cause I don't use it.

---

### Post by Regenweald on 2009-07-04
> **tad1073 said:**
> I just tried your way and am getting the same results.

What is the command to install a .deb via terminal?

Alpha 2 has been a smooth ride up until now.

```

sudo dpkg -i 'deb file'

```

Quick fingers taaviko :)

---

### Post by tad1073 on 2009-07-04
I just dropped to shell, re-installed the newest gdm, seems to have fixed having to login twice for now but window decorations always revert back to metacity, have to alt+f2 then emerald --replace

---

### Post by yelo3 on 2009-07-04
I'm still logged out during my session also with this new gdm. I have a small suspect it's related to session idle time

---

### Post by plun on 2009-07-04
> **autocrosser said:**
> Agreed--I am having problems as everyone else is--I get with it & get on the mailing list & do bug reports-- sign on to this one: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395313](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395313)

And i have a submit in on the dev-discuss-list....as soon as I get some info back, I'll post it.

My posting:


Thanks autocrosser....


GDM works OK for me and I am more concerned about strange functionality.

- It comes up with "Others"... what others ?  

- The greeter message warning  ?

- Extra step for a shutdown, first a logout.

- What conf-file controls this new GDM ?


Hopefully your mail can bring more light to this...

---

### Post by Darkshade on 2009-07-04
> **plun said:**
> Thanks autocrosser....


GDM works OK for me and I am more concerned about strange functionality.

- It comes up with "Others"... what others ?  

- The greeter message warning  ?

- Extra step for a shutdown, first a logout.

- What conf-file controls this new GDM ?


Hopefully your mail can bring more light to this...

- "Others" could be for users that are not included in the list maybe? (we're gonna need a settings menu to find out I guess)

- I don't get the warning either tbh.

- The extra step looks more like a bug than a feature..

- I want to say that there will be a menu to configure it like the old one but I'm a little afraid I might be wrong, so I guess we'll have to wait again.

---

### Post by plun on 2009-07-04
wayne_cat posted how the "warning" looks

[http://ubuntuforums.org/showpost.php?p=7553505&postcount=11](http://ubuntuforums.org/showpost.php?p=7553505&postcount=11)


How do I make a printscreen from a GDM screen  ????

---

### Post by 23meg on 2009-07-04
> **plun said:**
> 
How do I make a printscreen from a GDM screen  ????

If you mean a screenshot, Xephyr or Xnest can help.

---

### Post by plun on 2009-07-04
> **23meg said:**
> If you mean a screenshot, Xephyr or Xnest can help.

OK, thanks..... This bug is filed against this:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395324](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395324)

Probably the same as for a lot of us.


Search for a "Others"-bug....;)

---

### Post by plun on 2009-07-04
OFF-Topic warning, found a solution for a GDM screenshot.

[http://forums.linuxmint.com/viewtopic.php?f=55&t=20637&p=148487](http://forums.linuxmint.com/viewtopic.php?f=55&t=20637&p=148487)


The XNEST way seems to be broken.

[[img]http://ubuntu-pics.de/thumb/17759/screenshot_0gKy81.png[/img]](http://ubuntu-pics.de/bild/17759/screenshot_0gKy81.png)

;)

---

### Post by celticbhoy on 2009-07-04
I have installed and it works ok, but with some of the smaller issues mentioned. EXCEPT I have lost my panels. tried running gnome-panel from a terminal and it says it is running, but nothing on screen.

---

### Post by MacUntu on 2009-07-04
> **plun said:**
> The XNEST way seems to be broken.

Well, broken...

```
** (gdmflexiserver:12113): WARNING **: Not yet implemented
```

```
Application Options:
  -n, --xnest               Ignored - retained for compatibility
```

;)

---

### Post by gacb on 2009-07-04
Same Metacity error as Graaant - on both machines running a Karmic partition.

I recall a similar login issue with Intrepid that cropped up from time to time - it had to do with permissions on a particular file.

---

### Post by rudenko_ruslan on 2009-07-04
I have some weird problem with this new GDM - after entering sudo password (for the first time), I suddenly return to a login window (just like on plun's screen above). After this, when I'm again asked for sudo password, everything works OK (I mean, no sudden "returns" :) ).

So, have somebody encountered with this problem too?

P.S. Sorry for my poor english :(

---

### Post by autocrosser on 2009-07-04
There have been a couple of posts to dev-discuss-list---but no real answers yet---will keep everyone posted....

Next "bug" for people to sign in on---GDM 2.26x needs config panel similar to 2.20x : [http://bugzilla.gnome.org/show_bug.cgi?id=587750](http://bugzilla.gnome.org/show_bug.cgi?id=587750)

---

### Post by tjeremiah on 2009-07-04
hmm.. I actually like the shutdown option in the system menu now.

---

### Post by autocrosser on 2009-07-04
Config lack bug also filed in Launchpad: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395535](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395535)

Please confirm.......

---

### Post by buzzmandt on 2009-07-04
gdm is still being held back

---

### Post by scradock on 2009-07-04
> **autocrosser said:**
> There have been a couple of posts to dev-discuss-list---but no real answers yet---will keep everyone posted....

Next "bug" for people to sign in on---GDM 2.26x needs config panel similar to 2.20x : [http://bugzilla.gnome.org/show_bug.cgi?id=587750](http://bugzilla.gnome.org/show_bug.cgi?id=587750)
I'm still struggling to get GDM to do anything! 

I noticed an error message in the boot messages about failing to parse /etc/dbus-1/system.d/gdm.conf, so I wnt and looked at that file. It was clearly not a conf file, but a partial list of package information that must have been dumped when the install b0rked, so I deleted that. Re-booting without it did not give the error message, but still starts me in tty1.

Now I need to find out where to change that to tty7, I suppose.....

---

### Post by Vanishing on 2009-07-04
Strange, the new gdm logs me off randomly now....:mad:

---

### Post by taavikko on 2009-07-04
> **buzzmandt said:**
> gdm is still being held back

It's not held back.
It has new dependencies which cannot be fulfilled with "apt-get upgrade"
use "apt-get dist-upgrade" to satisfy them...

---

### Post by scradock on 2009-07-04
> **taavikko said:**
> AFAIK that editing /etc/default/console-setup isn't sufficient and need also to edit ../init.d/tty{3,4,5,6} by hand to prevent them from respawning.

enough from offtopic :)

This talk on "black screen" don't think it's due to the new GDM as my KDE is doing this too.
Difference is that the gdm respawns but KDE session is terminated. So would but my pointing two fingers in the X
I thought this part of the thread might help me set the boot sequence to end in tt7, but my /etc/init.d does not contain any files tty3, and so on. I have checked three installs, the Karmic 64-bit where I'm having GDM trouble, an un-upgraded Karmic 32-bit, and Jaunty 64-bit - none of them have ttyX files in /etc/init.d ????

Ah! it should be /etc/event.d ......

---

### Post by wayne_cat on 2009-07-04
> **Vanishing said:**
> Strange, the new gdm logs me off randomly now....:mad:

This happened to me when I removed metacity (apt-get remove metacity). There was an annoying error message ... have a look at this:

[http://ubuntuforums.org/showpost.php?p=7553505&postcount=11](http://ubuntuforums.org/showpost.php?p=7553505&postcount=11)

for a screenshot. So I reinstalled metacity and removed the file :

```
/usr/share/gdm/autostart/LoginWindow/metacity.desktop
```and the error message is gone and GDM stopped kicking me out.

---

### Post by buzzmandt on 2009-07-04
> **taavikko said:**
> It's not held back.
It has new dependencies which cannot be fulfilled with "apt-get upgrade"
use "apt-get dist-upgrade" to satisfy them...
worked like a charm.  no probs here with new gdm, except can't config it yet.  Even still using compiz without me mucking with it.
thanks

---

### Post by buzzmandt on 2009-07-04
> **tjeremiah said:**
> hmm.. I actually like the shutdown option in the system menu now.

I do too, and the system preferences where the fast-user-switcher used to be.  I really like it all

---

### Post by Vanishing on 2009-07-04
> **wayne_cat said:**
> This happened to me when I removed metacity (apt-get remove metacity). There was an annoying error message ... have a look at this:

[http://ubuntuforums.org/showpost.php?p=7553505&postcount=11](http://ubuntuforums.org/showpost.php?p=7553505&postcount=11)

for a screenshot. So I reinstalled metacity and removed the file :

```
/usr/share/gdm/autostart/LoginWindow/metacity.desktop
```and the error message is gone and GDM stopped kicking me out.

but for my case, metacity was not removed..o.o
gonna try to remove the file, i'll see if that works.:p
thanks a lot for the tip buddy!:p

---

### Post by wayne_cat on 2009-07-04
> **Vanishing said:**
> but for my case, metacity was not removed..o.o
gonna try to remove the file, i'll see if that works.:p
thanks a lot for the tip buddy!:p

Could you please post the result of your test.

BTW ... I have a lot of errors in the gdm logfiles (/var/log/gdm/*)

---

### Post by plun on 2009-07-04
My greeting error is gone after removing the metacity.desktop file...;)

---

### Post by rudenko_ruslan on 2009-07-04
> **plun said:**
> My greeting error is gone after removing the metacity.desktop file...;)
Yup, that helped me too.

---

### Post by wayne_cat on 2009-07-04
> **plun said:**
> My greeting error is gone after removing the metacity.desktop file...;)

> **rudenko_ruslan said:**
> Yup, that helped me too.

Switch to metacity after removing the file:

> metacity --replaceGnome hangs ... keyboard disabled ... mouse cursor gone :biggrin:

---

### Post by celticbhoy on 2009-07-04
Has anyone got compiz working with this.

---

### Post by wayne_cat on 2009-07-04
> **celticbhoy said:**
> Has anyone got compiz working with this.

No problems with compiz on my notebook.

---

### Post by plun on 2009-07-04
> **wayne_cat said:**
> Switch to metacity after removing the file:

Gnome hangs ... keyboard disabled ... mouse cursor gone :biggrin:

Well, I am not using Metacity....  running Compiz.):P

The error is gone but I notice a slowdown when browsing with Firefox-3.5

---

### Post by celticbhoy on 2009-07-04
> gary@Testing:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x600) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
compiz.real: intel_buffer_objects.c:103: intel_bufferobj_free: Assertion `!obj->Pointer' failed.
Aborted
gary@Testing:~$ 


Get this trying to run compiz....

---

### Post by Vanishing on 2009-07-04
> **wayne_cat said:**
> Could you please post the result of your test.

BTW ... I have a lot of errors in the gdm logfiles (/var/log/gdm/*)

apparently it fixed the login error, but still w8ing to see if gdm kicking me out or not.:lolflag:
thanks again buddy.

> Has anyone got compiz working with this.
I have no problem using compiz with the new gdm..:p

---

### Post by wayne_cat on 2009-07-04
> **celticbhoy said:**
> Get this trying to run compiz....

> compiz.real: intel_buffer_objects.c:103: intel_bufferobj_free: Assertion `!obj->Pointer' failed.

Seems to be a problem with xserver-xorg-video-intel :-k

---

### Post by buzzmandt on 2009-07-04
> **celticbhoy said:**
> Has anyone got compiz working with this.

compiz no problem here, acer aspire 3680, intel 950 mobile graphics

---

### Post by celticbhoy on 2009-07-04
> Seems to be a problem with xserver-xorg-video-intel 

Not for this thread then.

---

### Post by rudenko_ruslan on 2009-07-04
> **wayne_cat said:**
> Switch to metacity after removing the file:

Gnome hangs ... keyboard disabled ... mouse cursor gone :biggrin:
Switched to metacity, and now I can't enable "Desktop Effects" :) But no problems with keyboard, GNOME or mouse cursor. Rebooted - and compiz is alive :)

P.S. I noticed that after I removed "metacity.desktop" file, mouse cursor showing "busy" while logging in (GDM).

---

### Post by buzzmandt on 2009-07-04
> **rudenko_ruslan said:**
> I have some weird problem with this new GDM - after entering sudo password (for the first time), I suddenly return to a login window (just like on plun's screen above). After this, when I'm again asked for sudo password, everything works OK (I mean, no sudden "returns" :) ).

So, have somebody encountered with this problem too?

P.S. Sorry for my poor english :(

I'll confirm this one, but not in a terminal (sudo apt-get update worked fine) but the first time I was in a graphical environment and needed sudo password it threw me out.  was using synaptic manager.

---

### Post by rudenko_ruslan on 2009-07-04
> **buzzmandt said:**
> I'll confirm this one, but not in a terminal (sudo apt-get update worked fine) but the first time I was in a graphical environment and needed sudo password it threw me out.  was using synaptic manager.
Yeah, I forgot about "Computer Janitor" - there also were problems after typing password.

And I think that it's appearing not only after typing a password. I was going to "Submit Reply" there, but suddenly I was threwed out to GDM.

It's random thing, I suppose #-o

---

### Post by MacUntu on 2009-07-04
For me GDM won't start after booting because it's not the default login manager. 'dpkg-reconfigure gdm' doesn't show me the old dialog to choose the default login manager, 'dpkg-reconfigure xdm (or kdm)' shows only xdm and kdm:

[img]http://img.xrmb2.net/images/300009.png[/img]

---

### Post by scradock on 2009-07-04
Still struggling....

The problem seems to be a Permissions issue: after cleaning out garbage in the gdm logs (more Packages info!) and re-setting rw access to the /var/log/gdm folder (--T ???) I still get no gdm  on booting up.

So I tried running gdm from a terminal after logging in (on tty1) and starting X manually. I get:
```
gdm

** (gdm-binary:5701): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.47" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:5701): WARNING **: Could not acquire name; bailing out
sc@sc-laptop:/var/log/gdm$ 
```

or:
```
sudo gdm
............ 

** (gdm-binary:9237): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.50" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:9237): WARNING **: Could not acquire name; bailing out
sc@sc-laptop:/var/log/gdm$ 
```

My next question is: Which configuration file? A gdm.conf? Policykit?..??

Any ideas, anyone?

---

### Post by MacUntu on 2009-07-04
The 'T' means that the setgid-bit is set (and the x-bit isn't) - that's ok (I guess). Starting GDM with 'sudo gdm' works for me, though.

---

### Post by plun on 2009-07-04
> **MacUntu said:**
> For me GDM won't start after booting because it's not the default login manager. 'dpkg-reconfigure gdm' doesn't show me the old dialog to choose the default login manager, 'dpkg-reconfigure xdm (or kdm)' shows only xdm and kdm:


What gives a gdm reinstall  ?
```

sudo apt-get install --reinstall gdm
```

---

### Post by MacUntu on 2009-07-04
While running GDM: It kicked me out of the session. #-o Other than that it didn't help. Guess we/I'll have to wait for monday's updates to sort things out.

---

### Post by celticbhoy on 2009-07-04
Got my panels back, had to kill the original gnome-panel in sys-monitor then they re-started.

Just need to sort out video problem for Compiz now.

---

### Post by taavikko on 2009-07-04
One request, start a new thread on the problems, since there are few different bugs atm. and trying to read through this thread must give somebody a headache :)

This would help detailing the issues...

---

### Post by wayne_cat on 2009-07-04
> **scradock said:**
> Still struggling....

The problem seems to be a Permissions issue: after cleaning out garbage in the gdm logs (more Packages info!) and re-setting rw access to the /var/log/gdm folder (--T ???) I still get no gdm  on booting up.

So I tried running gdm from a terminal after logging in (on tty1) and starting X manually. I get:
```
gdm

** (gdm-binary:5701): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.47" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:5701): WARNING **: Could not acquire name; bailing out
sc@sc-laptop:/var/log/gdm$ 
```or:
```
sudo gdm
............ 

** (gdm-binary:9237): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.50" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:9237): WARNING **: Could not acquire name; bailing out
sc@sc-laptop:/var/log/gdm$ 
```My next question is: Which configuration file? A gdm.conf? Policykit?..??

Any ideas, anyone?

Related to d-bus

[http://markmail.org/message/vpaik7mkf2oouflm#query:is%20not%20allowed%20to%20own%20the%20service%20org.gnome.DisplayManager%20due%20to%20security%20policies%20in%20the%20configuration%20file+page:1+mid:cinmywknjldy5bo5+state:results](http://markmail.org/message/vpaik7mkf2oouflm#query:is%20not%20allowed%20to%20own%20the%20service%20org.gnome.DisplayManager%20due%20to%20security%20policies%20in%20the%20configuration%20file+page:1+mid:cinmywknjldy5bo5+state:results)

I have attached the file:

 /etc/dbus-1/system.d/gdm.conf

had to rename it to gdm.conf.txt to upload it ... do you have this file on your system?

---

### Post by celticbhoy on 2009-07-04
Yeah I got that file to.

---

### Post by wayne_cat on 2009-07-04
> **celticbhoy said:**
> Yeah I got that file to.

Do you have an entry for gdm in default-display-manager?

```
root@macbook:~# cat /etc/X11/default-display-manager
/usr/sbin/gdm
root@macbook:~# 
```

---

### Post by MacUntu on 2009-07-04
> **wayne_cat said:**
> Do you have an entry for gdm in default-display-manager? [...]


Thanks, that gave me my GDM autostart back. The question is: is that just a remnant of the old GDM or is it created by installing the new GDM.

**Edit:** Installing GDM neither changes the line in /etc/X11/default-display-manager (opposed to KDM/XDM) or creates it if missing (opposed to KDM/XDM). Guess I'll file a bug.

---

### Post by celticbhoy on 2009-07-04
Again I get the same result as you.

/usr/sbin/gdm

---

### Post by autocrosser on 2009-07-04
OK--I have been "rooting" around & have some information for everyone--I have not tried this stuff yet, so everyone---post what link helped/part of link/etc....

[http://live.gnome.org/GDM/2.22/Configuration](http://live.gnome.org/GDM/2.22/Configuration)

[http://hacktux.com/fedora/9/gdm](http://hacktux.com/fedora/9/gdm)

More bug report info: [http://bugzilla.gnome.org/show_bug.cgi?id=553250](http://bugzilla.gnome.org/show_bug.cgi?id=553250)

Information: 
[http://mail.gnome.org/archives/gdm-list/2009-April/msg00036.html](http://mail.gnome.org/archives/gdm-list/2009-April/msg00036.html)


Hang in there all;)

---

### Post by MacUntu on 2009-07-04
> **celticbhoy said:**
> Again I get the same result as you.

/usr/sbin/gdm

Do you have some .Xauthority-files in your home directory? If so, delete them and try again to run GDM with 'sudo gdm'. Just remembered seeing those error messages yesterday.

---

### Post by autocrosser on 2009-07-04
OK--here is the Schema options for /etc/gdm/custom.conf---not a lot to go on, but we have something...

[http://svn.gnome.org/viewvc/gdm/trunk/data/gdm.schemas.in.in?view=markup](http://svn.gnome.org/viewvc/gdm/trunk/data/gdm.schemas.in.in?view=markup)

The custom.conf.bak is the stock file---the custom.conf is my modded file....

---

### Post by celticbhoy on 2009-07-04
Just the .xauthority or the .Xsession stuff as well>

---

### Post by wayne_cat on 2009-07-04
> **MacUntu said:**
> Thanks, that gave me my GDM autostart back. The question is: is that just a remnant of the old GDM or is it created by installing the new GDM.

**Edit:** Installing GDM neither changes the line in /etc/X11/default-display-manager (opposed to KDM/XDM) or creates it if missing (opposed to KDM/XDM). Guess I'll file a bug.

AFAIK ... installing gdm does not mean, that gdm is automatically added to /etc/X11/default-display-manager

The function that adds gdm to this file is:

```
dpkg-reconfigure gdm

```The file default-display-manager is a part of Xorg so it should be there ... even if you have never installed kdm/gdm/xdm before.

---

### Post by celticbhoy on 2009-07-04
Deleted Xauthority, ran sudo gdm and got this :-

** (gdm-binary:4424): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:4424): WARNING **: Could not acquire name; bailing out

---

### Post by plun on 2009-07-04
> **autocrosser said:**
> OK--I have been "rooting" around & have some information for everyone--I have not tried this stuff yet, so everyone---post what link helped/part of link/etc....

[http://live.gnome.org/GDM/2.22/Configuration](http://live.gnome.org/GDM/2.22/Configuration)



Time to read manuals.....;)

Latest reference manual:

[http://library.gnome.org/admin/gdm/2.26/](http://library.gnome.org/admin/gdm/2.26/)

---

### Post by wayne_cat on 2009-07-04
> **celticbhoy said:**
> Deleted Xauthority, ran sudo gdm and got this :-

** (gdm-binary:4424): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:4424): WARNING **: Could not acquire name; bailing out

Try start gdm from a "real root"

```
sudo su -
/usr/sbin/gdm

```

---

### Post by celticbhoy on 2009-07-04
Same result.

Just so you are aware, wayne_cat, I dont have any problems with gdm, other than I cant get Compiz to run as it should.

---

### Post by MacUntu on 2009-07-04
> **wayne_cat said:**
> AFAIK ... installing gdm does not mean, that gdm is automatically added to /etc/X11/default-display-manager

With 2.20 it was like
* Having already installed another display manager like KDM: configuration dialog was shown
* Having no display manager installed: GDM got default.

Same for KDM and XDM, just not with GDM 2.26. dpkg-reconfigure doesn't change a thing for me. Maybe someone could change the content of /etc/X11/default-display-manager, run 'sudo dpkg-reconfigure gdm' and check if the file got updated? (If not, please confirm [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395591](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395591)).

---

### Post by wayne_cat on 2009-07-04
> **celticbhoy said:**
> Same result.

Just so you are aware, wayne_cat, I dont have any problems with gdm, other than I cant get Compiz to run as it should.

I'm sorry ... my mistake ... didn't saw, that your problem is not related to gdm :redface:

---

### Post by celticbhoy on 2009-07-04
Thats ok - glad to know the help was there!

---

### Post by scradock on 2009-07-04
> **MacUntu said:**
> With 2.20 it was like
* Having already installed another display manager like KDM: configuration dialog was shown
* Having no display manager installed: GDM got default.

Same for KDM and XDM, just not with GDM 2.26. dpkg-reconfigure doesn't change a thing for me. Maybe someone could change the content of /etc/X11/default-display-manager, run 'sudo dpkg-reconfigure gdm' and check if the file got updated? (If not, please confirm [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395591](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395591)).
Checked "sudo dpkg-reconfigure gdm" doesn't change the contents of /etc/X11/default-display-manager.

Looking at the Manual (thanks for the link) suggests that there are supposed to be a whole passle of scripts that are simply not there in /etc/gdm as of now.

---

### Post by wayne_cat on 2009-07-04
> **MacUntu said:**
> With 2.20 it was like
* Having already installed another display manager like KDM: configuration dialog was shown
* Having no display manager installed: GDM got default.

Same for KDM and XDM, just not with GDM 2.26. dpkg-reconfigure doesn't change a thing for me. Maybe someone could change the content of /etc/X11/default-display-manager, run 'sudo dpkg-reconfigure gdm' and check if the file got updated? (If not, please confirm [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395591](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395591)).

Confirmed

Thank you for creating the bug report.

---

### Post by scradock on 2009-07-04
Thanks wayne_cat - /etc/dbus-1/system.d/gdm.conf was one of the files that got scrambled and filled with Pacages info. I'll see what happens with the copy you sent......

---

### Post by scradock on 2009-07-04
> **scradock said:**
> Thanks wayne_cat - /etc/dbus-1/system.d/gdm.conf was one of the files that got scrambled and filled with Pacages info. I'll see what happens with the copy you sent......
OK - nearly there! The gdm.conf didn't do the trick, but the error messages are getting more helpful.

I have checked all the files installed on July 3rd and found the following are all garbage:  /etc/gdm/gdm.schemas, custom.conf and Xsession
          /etc/X11/default-display-manager
          /etc/dbus-1/system.d/gdm.conf

There may be others! So far I have replacement copies of eveything but gdm.schemas, and trying to run without that gives an error saying....it can't run without that.

So could someone please post me a copy of /etc/gdm/gdm.schemas? Reinstalling doesn't seem to regenerate it if it's missing - another bug, in my mind....

---

### Post by scradock on 2009-07-04
I've tried using the custom.conf that autocrosser posted earlier as gdm.schemas - it works in so far as the error message about not working without gdm.schemas doesn't appear.

But I still get the following error message when I run "sudo gdm" from the tty1 after login. (No X has yet started, as far as I know).

```
**
ERROR:gdm-settings-direct.c:189:gdm_settings_direct_get_string: assertion failed: (entry != NULL)
Aborted
```

I've removed Xauthority from ~, replaced /etc/gdm/Xsession from /etc/X11, replaced /etc/dbus-1/system.d/gdm.conf with the one sent by wayne_cat, edited /etc/X11/default-display-manager to read "/sur/sbin/gdm"...

Anyone got a gdm.schemas that works?

---

### Post by wayne_cat on 2009-07-04
this is a complete backup of /etc/gdm

```
cd /etc
tar -cpvf /tmp/gdm.tar gdm
```you can find the file inside

```
root@macbook:/etc/gdm# ls -lah
total 48K
drwxr-xr-x   6 root root 4.0K Jul  4 23:09 .
drwxr-xr-x 169 root root  12K Jul  4 23:10 ..
drwxr-xr-x   2 root root 4.0K Jul  3 21:46 Init
drwxr-xr-x   2 root root 4.0K Jul  3 21:46 PostLogin
drwxr-xr-x   2 root root 4.0K Jul  3 21:46 PostSession
drwxr-xr-x   2 root root 4.0K Jul  3 21:46 PreSession
-rwxr-xr-x   1 root root 6.2K Jul  2 17:02 Xsession
-rw-r--r--   1 root root  105 Jul  3 00:05 custom.conf
-rw-r--r--   1 root root 2.5K Jul  2 17:02 gdm.schemas
root@macbook:/etc/gdm# 

```

---

### Post by scradock on 2009-07-04
Thanks so much - that should do the trick!

---

### Post by scradock on 2009-07-04
At last! I have seen the new login screen!

Thanks for all the help. It appears that the initial partial install filled a whole bunch of files with bits of the Package list instead of the correct information.

Now to find some actual bugs.... it hasn't stopped compiz working so far!

I had added the Log-out applet to the top panel in place of fast-user-switcher, but now that gdm is actually working it has stopped functioning correctly. On selecting Log Out from the options given I get a black screen freeze - no response to keyboard or trackpad inputs, not even [Alt]-[SysRq]-REISUB

The background to the Log-in box is the standard brown streaks wallpaper - can I change this? How? It's not apparently in gdm.schemas.......

---

### Post by wayne_cat on 2009-07-04
you can find the gdm background image with:

```
root@macbook:~# gconftool-2 --get /desktop/gnome/background/picture_filename
/usr/share/backgrounds/warty-final-ubuntu.png

```

---

### Post by autocrosser on 2009-07-04
> **wayne_cat said:**
> you can find the gdm background image with:

```
root@macbook:~# gconftool-2 --get /desktop/gnome/background/picture_filename
/usr/share/backgrounds/warty-final-ubuntu.png

```

Looks like it is hard-coded somewhere--I changed my background & the login stayed with warty--then I renamed another .png to warty-final-ubuntu.png & it was used.....

---

### Post by scradock on 2009-07-04
> **autocrosser said:**
> Looks like it is hard-coded somewhere--I changed my background & the login stayed with warty--then I renamed another .png to warty-final-ubuntu.png & it was used.....
Yes, that gets the desktop background file-name. But what I want is the file-name for the background file used behind the Log-in by GDM. 

Again, it's probably hard-coded somewhere, but I've been trying changing file names in /usr/share/gdm/themes and getting no joy.....

---

### Post by wayne_cat on 2009-07-04
yes ... the new gdm and women ... with all these mysterious inner workings ... hard to understand ... but it is so easy to love them :biggrin:

---

### Post by tad1073 on 2009-07-04
How would I go about un-installing the new gdm and installing the old gdm from the live cd?

---

### Post by scradock on 2009-07-04
Ah yes! It needs to be called warty-final-ubuntu.png, whatever the filename is for the actual desktop background. That really IS hard-coding....

Now it's pretty seamless, which is nice.

One step forward....

---

### Post by wayne_cat on 2009-07-04
> **tad1073 said:**
> How would I go about un-installing the new gdm and installing the old gdm from the live cd?

You can download the old version from here:

[http://archive.ubuntu.com/ubuntu/pool/main/g/gdm/](http://archive.ubuntu.com/ubuntu/pool/main/g/gdm/)

remove the new gdm with

```
sudo apt-get remove --purge gdm

```and install the downloaded deb

```
sudo dpkg -i gdm_2.20.10-0ubuntu2_i386.deb
```But you have to exclude gdm from "apt-get upgrade" ... have a look at this:

[http://ubuntuforums.org/showthread.php?t=375194](http://ubuntuforums.org/showthread.php?t=375194)

---

### Post by autocrosser on 2009-07-04
Everyone "should" take a look at bug--- [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395299](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395299)  --I have a dialog going with Sebastien--maybe we can get a simple Config panel going soon........

---

### Post by tjeremiah on 2009-07-04
can anyone show how it may look once done?

---

### Post by wayne_cat on 2009-07-04
> **tjeremiah said:**
> can anyone show how it may look once done?

the new "design" of gdm 2.26?

---

### Post by autocrosser on 2009-07-04
I'm doing a mockup--will post with it soon......

---

### Post by tad1073 on 2009-07-04
> **wayne_cat said:**
> You can download the old version from here:

[http://archive.ubuntu.com/ubuntu/pool/main/g/gdm/](http://archive.ubuntu.com/ubuntu/pool/main/g/gdm/)

remove the new gdm with

```
sudo apt-get remove --purge gdm

```and install the downloaded deb

```
sudo dpkg -i gdm_2.20.10-0ubuntu2_i386.deb
```But you have to exclude gdm from "apt-get upgrade" ... have a look at this:

[http://ubuntuforums.org/showthread.php?t=375194](http://ubuntuforums.org/showthread.php?t=375194)

That didn't work, errors installing, not compatable with X11, unmet dependancies, so I just re-installed the new gdm and will deal with the issues until a fix is uploaded.

---

### Post by wayne_cat on 2009-07-04
> **tad1073 said:**
> That didn't work, errors installing, not compatable with X11, unmet dependancies, so I just re-installed the new gdm and will deal with the issues until a fix is uploaded.

Sorry ... I forgot that gdm came with the Xorg updates :(

The Ubuntu developers behind gdm are quite active ... they know that there are some problems so I'm sure we will get a solution in a view days.

PS ... autocrosser, thank you for talking with Sebastien Bacher.

---

### Post by ktp on 2009-07-04
> **tjeremiah said:**
> hmm.. I actually like the shutdown option in the system menu now.

You get the shutdown options in the system menu, even in 9.04, if you remove the Fast User Switch Applet.

---

### Post by autocrosser on 2009-07-04
OK--stupid--simple idea for basic settings--one list view--for default user--two on/off checkboxes--set so they can't both be on at the same time & a way to change the background....not much but I think it would be fairly easy to code......

---

### Post by wayne_cat on 2009-07-04
I'm missing my gdm theme but an option to set a background image and a default user is "everything that I really need" to be happy. The "auto-login" is a useful option to "hide" gdm until we have a final version. "timed login" ... ok ... you want to add some bling/luxury :biggrin:

Edit: something I forgot ... would it be a problem to add an option: "activate gdm in /etc/X11/default-display-manager"?

---

### Post by autocrosser on 2009-07-04
Well-I was going off of the default settings that you can change by manual edit of the custom.conf in /etc/gdm--it sounds like no-one wants to really do the heavy-lifting to build a full-featured panel like the old one (at least not now)--what I am proposing would really just edit the one file--but I am hoping that it would not be very hard to change the background--I just don't know where it is hard-coded right now--so--hey, always ask for something extra ;)

I don't know what is involved with your one--I don't see it in the basic settings.....you could goto the bug reports & add to the request.........

---

### Post by buzzmandt on 2009-07-04
> **wayne_cat said:**
> I'm missing my gdm theme but an option to set a background image and a default user is "everything that I really need" to be happy. The "auto-login" is a useful option to "hide" gdm until we have a final version. "timed login" ... ok ... you want to add some bling/luxury :biggrin:

Edit: something I forgot ... would it be a problem to add an option: "activate gdm in /etc/X11/default-display-manager"?

I really like the timed login, just a few seconds to have the option to change user without having to type full login information if I don't.  If the options not there then I'll just use auto login, no big deal.  just wanted it known

---

### Post by autocrosser on 2009-07-04
Well--right now you can manual edit it in--I did--but I want something that is at least a shadow of what we had before.....

---

### Post by wayne_cat on 2009-07-04
Hmmm ... tried to find a linux distribution with gdm 2.26 + "customizing login screen options via menu" ... without success.

What is wrong with the old gdm version ... it works ... you can configure it ... there are many themes for it on gnomelook ... is gdm 2.26 really a good idea?

---

### Post by tjeremiah on 2009-07-04
> **wayne_cat said:**
> Hmmm ... tried to find a linux distribution with gdm 2.26 + "customizing login screen options via menu" ... without success.

What is wrong with the old gdm version ... it works ... you can configure it ... there are many themes for it on gnomelook ... is gdm 2.26 really a good idea?

I like it. Though im waiting for a more easy way to customize.

---

### Post by 23meg on 2009-07-04
> **wayne_cat said:**
> is gdm 2.26 really a good idea?

Short answer: [Yes]("http://live.gnome.org/GDM/NewDesign").

Longer answer: Regardless of whether it's a good idea to ship it in Karmic or not, it's a good idea to test it in the Karmic development cycle, since given that Karmic+1 is most likely going to be a long term support release, and the new GDM is going to have to be supported for its lifecycle, we (as well as upstream) can benefit from the extra testing.

---

### Post by wayne_cat on 2009-07-04
> **tjeremiah said:**
> I like it. Though im waiting for a more easy way to customize.

I also like the new look (and the smooth fading) but:

[http://mail.gnome.org/archives/gdm-list/2009-April/msg00036.html](http://mail.gnome.org/archives/gdm-list/2009-April/msg00036.html)

- no gdm-greater XML themes (Delete gnomelook gdm themes from your bookmarks)
- configuration with gconf-editor aka "linux regedit.exe" 

is this a step forward?

[COLOR=Red]edit: please read [http://ubuntuforums.org/showpost.php?p=7563333&postcount=190](http://ubuntuforums.org/showpost.php?p=7563333&postcount=190)[/COLOR]

---

### Post by scradock on 2009-07-05
> **autocrosser said:**
> Well-I was going off of the default settings that you can change by manual edit of the custom.conf in /etc/gdm--it sounds like no-one wants to really do the heavy-lifting to build a full-featured panel like the old one (at least not now)--what I am proposing would really just edit the one file--but I am hoping that it would not be very hard to change the background--I just don't know where it is hard-coded right now--so--hey, always ask for something extra ;)

I don't know what is involved with your one--I don't see it in the basic settings.....you could goto the bug reports & add to the request.........
So let us into the secret - how do you set Autologin instead of TimedLogin? Simply changing the words didn't do it for me.....

---

### Post by Darkshade on 2009-07-05
Nice ideas, Autocrosser! I would only add an option to show or hide the bottom panel - I personally find it very annoying, maybe because I use gnome-do with the docky interface, people who actually have a panel there might find it normal. Just another checkbox for the panel (see attachment) and someone to actually make it real :p

---

### Post by wayne_cat on 2009-07-05
> **scradock said:**
> So let us into the secret - how do you set Autologin instead of TimedLogin? Simply changing the words didn't do it for me.....

[http://library.gnome.org/admin/gdm/2.26/gdm.html#configuration](http://library.gnome.org/admin/gdm/2.26/gdm.html#configuration)

Have you configured the User?
```


**[daemon]**

AutomaticLoginEnable=true
[COLOR=Red]AutomaticLogin=scradock[/COLOR]
```

---

### Post by scradock on 2009-07-05
> **wayne_cat said:**
> [http://library.gnome.org/admin/gdm/2.26/gdm.html#configuration](http://library.gnome.org/admin/gdm/2.26/gdm.html#configuration)

Have you configured the User?
```


**[daemon]**

AutomaticLoginEnable=true
[COLOR=Red]AutomaticLogin=scradock[/COLOR]
```
Yes, I'd got that far, but it didn't work the first time I tried restarting. Maybe another try will do.

I also noticed that the Configuration document you linked there says that the background can be configured in gconf, but does not specify the settings under /schemas/apps/gdm/simple-greeter/settings-manager-plugins/background that are needed to do this. The only things set at the moment are "active" <schema> and "priority" <schema>. These cannot be changed in gconf-editor.

However, in /usr/share/gconf/schemas there is gdm-simple-greeter.schemas, which should be where the schemas are actually set, since they cannot be changed in gconf-editor. However, the background section doesn't contain a key for the background file name, and other settings I've tried changing don't reflect either in gconf or in the behavior of the simple greeter.

---

### Post by buzzmandt on 2009-07-05
> **scradock said:**
> So let us into the secret - how do you set Autologin instead of TimedLogin? Simply changing the words didn't do it for me.....

make sure you're editing the conf-custom file
   /etc/gdm/gdm.conf-custom
worked for me

---

### Post by scradock on 2009-07-05
> **buzzmandt said:**
> make sure you're editing the conf-custom file
   /etc/gdm/gdm.conf-custom
worked for me
Ahah! that was it - I had a custom.conf file, which I was editing - didn't realise it was the wrong one. Still, now it logs in atomatically, which means I don't need to keep trying to chnage the background for the simple greeter......

---

### Post by autocrosser on 2009-07-05
> **Darkshade said:**
> Nice ideas, Autocrosser! I would only add an option to show or hide the bottom panel - I personally find it very annoying, maybe because I use gnome-do with the docky interface, people who actually have a panel there might find it normal. Just another checkbox for the panel (see attachment) and someone to actually make it real :p

Yes--yours is much prettier than mine--I just dashed off a quick thought & didn't bother to make it look good :)  You might submit it to the two bug reports--perhaps a polished one will prompt faster service;)

---

### Post by autocrosser on 2009-07-05
> **scradock said:**
> Ahah! that was it - I had a custom.conf file, which I was editing - didn't realise it was the wrong one. Still, now it logs in atomatically, which means I don't need to keep trying to chnage the background for the simple greeter......

To clarify--I modify both files the same---gdm-custom is the file that is being phased out & custom phased in---so keep both with the same data for when the old file is removed for good.......

---

### Post by scradock on 2009-07-05
> **autocrosser said:**
> To clarify--I modify both files the same---gdm-custom is the file that is being phased out & custom phased in---so keep both with the same data for when the old file is removed for good.......
Owww! that's crazy! Now we have about 6 config files, all supposed to control the simple-greeter, and we have to keep tabs on which ones are being used today but not tomorrow, which ones yesterday but not today, and which ones will maybe be used next week so they had better be ready?

Count them - /etc/gdm/gdm.conf; gdm.conf-custom; custom.conf; /etc/gconf/schemas/gdm-simple-greeter.schemas; /etc/dbus-1/system.d/gdm.conf (for Policykit?) and whatever gconf keeps its non-schema information for gdm in!!!!

And the configuration guide says blandly that gconf allows us to specify the background file name.......but not how!

---

### Post by autocrosser on 2009-07-05
And the developers don't understand why I want a settings panel.............:lolflag:

---

### Post by scradock on 2009-07-05
The default background file is specified in /usr/share/gconf/defaults/16_ubuntu-wallpapers. It's set to warty-final-ubuntu.png; I'm changing it there, and expect it to appear as the background to the simple greeter....

---

### Post by scradock on 2009-07-05
> **scradock said:**
> The default background file is specified in /usr/share/gconf/defaults/16_ubuntu-wallpapers. It's set to warty-final-ubuntu.png; I'm changing it there, and expect it to appear as the background to the simple greeter....
Nope - it still brings up the original warty-final-ubuntu.png with the greeter. So there has to be yet another file or key where the name can be changed........

---

### Post by Darkshade on 2009-07-05
> **autocrosser said:**
> Yes--yours is much prettier than mine--I just dashed off a quick thought & didn't bother to make it look good :)  You might submit it to the two bug reports--perhaps a polished one will prompt faster service;)

Well, I was just going to add some text to your mockup but then I started messing with Photoshop (I'm also working on a GTK theme and I thought some good idea might come up while doing the mockup but had no luck) and decided to post it anyway :D

I'm having some trouble logging into my launchpad account, if you think it'll help faster development feel free to submit it if you're not too busy :)

---

### Post by scradock on 2009-07-05
There's another default background file specified in /usr/share/gconf/schemas/desktop_gnome_background.schemas, but it was set to a non-existent file. I set it to the file I want, not really expecting it to work.

It didn't.

At the moment the only way to get the desired file as background appears to be to rename it to warty-final-ubuntu.png.

Which is ridiculous!

[But it works....]

---

### Post by MacUntu on 2009-07-05
Was your gdm-simple-greeter.schemas registered when updating to GDM 2.26? Mine wasn't and I had to run 'sudo gconf-schemas --register gdm-simple-greeter.schemas' to get the keys at /apps/gdm/simple-greeter.

Edit: Nevermind, right now those keys don't seem to have any influence on the greeter's behavior.

---

### Post by Bou on 2009-07-05
Dumb question maybe: would it be possible for the GDM background to fade into the desktop background, like they do when you set one manually in the appearance properties dialogue?

---

### Post by Eclipse. on 2009-07-05
> **wayne_cat said:**
> Hmmm ... tried to find a linux distribution with gdm 2.26 + "customizing login screen options via menu" ... without success.

What is wrong with the old gdm version ... it works ... you can configure it ... there are many themes for it on gnomelook ... is gdm 2.26 really a good idea?

It will get better obviously before the release, chill out.Things need to be broken sometimes to make the overall product better.;)

---

### Post by tad1073 on 2009-07-05
youtube video of my boot process with grub2 and new GDM
[http://www.youtube.com/watch?v=_SM7jYphZ7U](http://www.youtube.com/watch?v=_SM7jYphZ7U)

---

### Post by autocrosser on 2009-07-05
> **Bou said:**
> Dumb question maybe: would it be possible for the GDM background to fade into the desktop background, like they do when you set one manually in the appearance properties dialogue?

Well--right now the greeter wallpaper seems to be hard-coded to /usr/share/backgrounds/warty-final-ubuntu.png

You can replace that .png with your desktop image & have a seamless fade-in. Scradock & I are looking as to where the .png is coded in--so there can be a config line change to do that.....

---

### Post by Bou on 2009-07-05
> **autocrosser said:**
> Well--right now the greeter wallpaper seems to be hard-coded to /usr/share/backgrounds/warty-final-ubuntu.png

You can replace that .png with your desktop image & have a seamless fade-in. Scradock & I are looking as to where the .png is coded in--so there can be a config line change to do that.....

Well, that's not exactly what I meant: I was referring to have a fade-in effect BETWEEN the GDM background and the desktop background.

---

### Post by tjeremiah on 2009-07-05
> **Bou said:**
> Well, that's not exactly what I meant: I was referring to have a fade-in effect BETWEEN the GDM background and the desktop background.

that would be cool.

---

### Post by scradock on 2009-07-05
> **MacUntu said:**
> Was your gdm-simple-greeter.schemas registered when updating to GDM 2.26? Mine wasn't and I had to run 'sudo gconf-schemas --register gdm-simple-greeter.schemas' to get the keys at /apps/gdm/simple-greeter.

Edit: Nevermind, right now those keys don't seem to have any influence on the greeter's behavior.
Maybe it's gconf that needs an update - there's a note that the schemas can't be edited from the gconf-editor.....

---

### Post by autocrosser on 2009-07-05
Well--I just finished building a sandboxed clean install of GDM from a gnome 2.26 .tar--put it into /opt so I could look at it. Don't see anywhere that you can define the background image :mad:

I'm going to remove all of it & build our version in the same sandbox to look.......

---

### Post by cdahmedeh on 2009-07-05
> **Bou said:**
> Well, that's not exactly what I meant: I was referring to have a fade-in effect BETWEEN the GDM background and the desktop background.

I remember seeing that feature in Fedora 10 and 11. The same fading was seen in the first alpha's of Jaunty. However, it was then removed because it apparently added 2 seconds to the login time. Anyone can confirm this ?

---

### Post by MacUntu on 2009-07-05
> **cdahmedeh said:**
> The same fading was seen in the first alpha's of Jaunty. However, it was then removed because it apparently added 2 seconds to the login time. Anyone can confirm this ?

IIRC it was: GDM - solid color - fade to desktop.

---

### Post by scradock on 2009-07-05
DOH!!!! 

IF there is a file /usr/share/backgrounds/warty-final-ubuntu.png it gets used as the simple-greeter background. But if there isn't?????

I simply renamed it, and gdm sensibly selects the file I have as my background in Preferences | Appearance | Backgrounds.........

Seamless!

---

### Post by wayne_cat on 2009-07-05
gdm 2.26 uses these settings for the current theme (that cannot be changed atm)

```
1. the background image

/usr/share/backgrounds/warty-final-ubuntu.png

``````
2. the icon above the hostname (the computer icon)

/usr/share/icons/Human/scalable/devices/computer.svg
``````
3. the user icon

/usr/share/icons/gnome/scalable/stock/generic/stock_person.svg

``````
4. the color scheme

/usr/share/themes/Human/gtk-2.0/gtkrc

```I don't use the Human theme ... so I have changed the icons and the color scheme :biggrin:

---

### Post by autocrosser on 2009-07-05
> **scradock said:**
> DOH!!!! 

IF there is a file /usr/share/backgrounds/warty-final-ubuntu.png it gets used as the simple-greeter background. But if there isn't?????

I simply renamed it, and gdm sensibly selects the file I have as my background in Preferences | Appearance | Backgrounds.........

Seamless!

GREAT!!! I'll check that out--I use Wallpaper Tray to change my desktop--so maybe I'll have a different wallpaper each time I use the greeter--Very Interesting......

---

### Post by wayne_cat on 2009-07-05
> **autocrosser said:**
> GREAT!!! I'll check that out--I use Wallpaper Tray to change my desktop--so maybe I'll have a different wallpaper each time I use the greeter--Very Interesting......

did it work ... i have renamed the file ... but now I have no background picture ... the background is just filled with the default color (defined in the gtkrc file)

---

### Post by scradock on 2009-07-05
> **wayne_cat said:**
> gdm 2.26 uses these settings for the current theme (that cannot be changed atm)

```
1. the background image

/usr/share/backgrounds/warty-final-ubuntu.png

``````
2. the icon above the hostname (the computer icon)

/usr/share/icons/Human/scalable/devices/computer.svg
``````
3. the user icon

/usr/share/icons/gnome/scalable/stock/generic/stock_person.svg

``````
4. the color scheme

/usr/share/themes/Human/gtk-2.0/gtkrc

```I don't use the Human theme ... so I have changed the icons and the color scheme :biggrin:
Great info!

Now #2 on the list CAN be changed - it's in the schema /usr/share/gconf/schemas/gdm-simple-greeter.schemas; I replaced "computer" with "gnome-dev-cdrom" to get a nive ico of a ... cdrom.

Presumably the colors can be changed the same way - or did you do something else?

BUT there is no key "background image file" in the schema, and the two possible names I've tried for it (filename and BackgroundImage) in gconf-editor haven't done the trick.

But simply NOT having warty-final-ubuntu.png in /usr/share/backgrounds works for me...

---

### Post by scradock on 2009-07-05
> **wayne_cat said:**
> did it work ... i have renamed the file ... but now I have no background picture ... the background is just filled with the default color (defined in the gtkrc file)
Sounds as if the background shuffler is working on top of a static color, which gdm is picking up.....

---

### Post by plun on 2009-07-05
I post this one again.... maybe its useful...;)

[http://library.gnome.org/admin/gdm/2.26/configuration.html.en](http://library.gnome.org/admin/gdm/2.26/configuration.html.en)


--

---

### Post by autocrosser on 2009-07-05
I wish--I've been over & over that one----still not telling me the things I want to know :mad:

Found out if I delete the warty png--I only get the solid colour background whilst running Wallpaper Tray....was hoping that the greeter would pickup the changed wallpaper every time.......

---

### Post by ronacc on 2009-07-05
where did the "options" choice go on the greeter window "? I went to switch to a E17 session and couldn't find where to switch sessions .

---

### Post by wayne_cat on 2009-07-05
There should be a option to chose the session:

[http://www.nabble.com/gdm-2.26-default-session-td23373277.html](http://www.nabble.com/gdm-2.26-default-session-td23373277.html)

but I can't see it ... Karmic gdm 2.26 seems to be "hard coded to start gnome" version ;)

---

### Post by plun on 2009-07-05
> **autocrosser said:**
> I wish--I've been over & over that one----still not telling me the things I want to know :mad:

Found out if I delete the warty png--I only get the solid colour background whilst running Wallpaper Tray....was hoping that the greeter would pickup the changed wallpaper every time.......

This  gconf key

```
apps/gdm/simple-greeter/settings-manager-plugins/background/active

Set to True to enable the background settings manager plugin.
```

Somewhere we should have a plugin for the background...????

---

### Post by wayne_cat on 2009-07-05
> **wayne_cat said:**
> There should be a option to chose the session:

[http://www.nabble.com/gdm-2.26-default-session-td23373277.html](http://www.nabble.com/gdm-2.26-default-session-td23373277.html)

but I can't see it ... Karmic gdm 2.26 seems to be "hard coded to start gnome" version ;)

I was wrong .. you have to create a file:

/usr/share/xsessions/E17.desktop

have a look at the gnome.desktop file in the folder ... should be easy to write a file for E17

---

### Post by autocrosser on 2009-07-05
> **plun said:**
> This  gconf key

```
apps/gdm/simple-greeter/settings-manager-plugins/background/active

Set to True to enable the background settings manager plugin.
```Somewhere we should have a plugin for the background...????


Would be nice---but I have that one set already & no change.....In other words--it is not working........I looked at that key yesterday.

More info--I just unset the key & logged out/in--It still wants to use the warty.png that I modded....Looks like more hard-coding going on....

---

### Post by scradock on 2009-07-05
> **autocrosser said:**
> Would be nice---but I have that one set already & no change.....In other words--it is not working........I looked at that key yesterday.

More info--I just unset the key & logged out/in--It still wants to use the warty.png that I modded....Looks like more hard-coding going on....
Yes - that should make it work, but there also needs to be a key under /apps/gdm/simple-greeter/settings-manager-plugins/backgrounds that sets the file name! And we don't know what to call it, and if the name is wrong it's ignored...

Dear Plun, can you find the part of the administration documentation that tells us what to call this key? I've looked, autocrosser has looked, and we can't find it.....

---

### Post by plun on 2009-07-05
> **scradock said:**
> 

Dear Plun, can you find the part of the administration documentation that tells us what to call this key? I've looked, autocrosser has looked, and we can't find it.....

Nope... according to the gconf key there should be a background manager plugin.

From the manual:

> **5.8.&#8195;GNOME Settings Daemon**

GDM enables the following gnome-settings-daemon plugins: a11y-keyboard, **background**, sound, xsettings.

**These are responsible for things like the background image**, font and theme settings, sound events, etc.

Plugins can also be disabled using GConf. For example, if you want to disable the sound plugin then unset the following key: /apps/gdm/simple-greeter/settings-manager-plugins/sound/acti


:^o:-\"

---

### Post by autocrosser on 2009-07-05
> **plun said:**
> Nope... according to the gconf key there should be a background manager plugin.:^o:-\"

Yes--that is what I looked at also--pity that there is not a key to set the default image.....maybe a bug report time.....

---

### Post by plun on 2009-07-05
> **autocrosser said:**
> Yes--that is what I looked at also--pity that there is not a key to set the default image.....maybe a bug report time.....

Probably hardcoded within this file....

/usr/lib/gnome-settings-daemon-2.0/libbackground.so

Thats the plugin....;)   or crack it from source...;)

---

### Post by ronacc on 2009-07-05
> **wayne_cat said:**
> I was wrong .. you have to create a file:

/usr/share/xsessions/E17.desktop

have a look at the gnome.desktop file in the folder ... should be easy to write a file for E17

there is already an enlightenment.desktop  file in /usr/share/xsessions/ .  and still no "options" shown , thinking this might be because I was set for "timed login" I went to change that but the "login window" entry is gone from system>administration ,when the login window comes up it says "automatic login" even though I had specificly set it to "timed login" to allow me to select the session I wanted .

---

### Post by scradock on 2009-07-05
OK - next problem!

Somewhat spoiling the seamless transition from Login Window to Desktop is a nasty box that comes up saying:
```
These windows do not support "save current settings" and will have to be restarted next time you log in

Class: Login Window
Window: Gdm-simple-greeter

Cancel button
OK button
```

I've made sure I don't have autosave selected for my session.

It only takes one click to dismiss it, but it hangs around while I'm trying to do other things, as it won't go away until it feels like it....

Any ideas?

---

### Post by MacUntu on 2009-07-05
> **scradock said:**
> Any ideas?

Yes. Use Launchpad's search function! :D

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395324](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395324)

---

### Post by wayne_cat on 2009-07-05
> **scradock said:**
> OK - next problem!

Somewhat spoiling the seamless transition from Login Window to Desktop is a nasty box that comes up saying:
```
These windows do not support "save current settings" and will have to be restarted next time you log in

Class: Login Window
Window: Gdm-simple-greeter

Cancel button
OK button
```I've made sure I don't have autosave selected for my session.

It only takes one click to dismiss it, but it hangs around while I'm trying to do other things, as it won't go away until it feels like it....

Any ideas?

remove the file:

```
/usr/share/gdm/autostart/LoginWindow/metacity.desktop
```

---

### Post by plun on 2009-07-05
> **scradock said:**
> OK - next problem!



Any ideas?


Yup, this bug discussed somewhere within this thread...;)

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395324](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395324)

Remove:
/usr/share/gdm/autostart/LoginWindow/metacity.desktop

---

### Post by scradock on 2009-07-05
Thanks MacUntu, wayne_cat and plun - removing metacity.desktop did the trick!

Now I just need to find out how to allow NetworkManager to start up without asking for an AdminAuthorization.....

---

### Post by wayne_cat on 2009-07-05
> **ronacc said:**
> there is already an enlightenment.desktop  file in /usr/share/xsessions/ .  and still no "options" shown , thinking this might be because I was set for "timed login" I went to change that but the "login window" entry is gone from system>administration ,when the login window comes up it says "automatic login" even though I had specificly set it to "timed login" to allow me to select the session I wanted .

The   gdm 2.26 update has removed the configuration program ... you have to edit the file:
 
```
/etc/gdm/gdm.schemas
```I have attached the file from my system. I have created a E17.desktop file and get a "choose option" in gdm

edit: the chooser only appears if you select a user ... click on your user ... the chooser appears ... select E17 from the chooser ... enter your password ... click on OK

---

### Post by wayne_cat on 2009-07-05
ronnac,

this is what it should look like:

[[IMG]http://ubuntu-pics.de/thumb/17921/gdm_screenshot_YG86Zj.png[/IMG]]("http://ubuntu-pics.de/bild/17921/gdm_screenshot_YG86Zj.png")

---

### Post by ronacc on 2009-07-05
thanks that got it .

---

### Post by scradock on 2009-07-05
> **wayne_cat said:**
> The   gdm 2.26 update has removed the configuration program ... you have to edit the file:
 
```
/etc/gdm/gdm.schemas
```I have attached the file from my system. I have created a E17.desktop file and get a "choose option" in gdm

edit: the chooser only appears if you select a user ... click on your user ... the chooser appears ... select E17 from the chooser ... enter your password ... click on OK
So how do we stop using /etc/gdm/custom.conf or gdm.conf-custom (whichever one it is) and "activate" gdm.schemas? I tried putting it into /usr/share/gconf/schemas, but it has incorrect syntax and root node. Do we just delete the other conf files?

---

### Post by wayne_cat on 2009-07-05
> **scradock said:**
> So how do we stop using /etc/gdm/custom.conf or gdm.conf-custom (whichever one it is) and "activate" gdm.schemas? I tried putting it into /usr/share/gconf/schemas, but it has incorrect syntax and root node. Do we just delete the other conf files?

From the gdm 2.26 documentation:

```
The GDM daemon is configured using the <etc>/gdm/custom.conf file.  
Default values are stored in GConf in the gdm.schemas file.  It is recommended 
that end-users modify the /etc/gdm/custom.conf file because the schemas file may 
be overwritten when the user updates their system tohave a newer version of GDM.       
```IMHO ... the settings from custom.conf (gdm-custom.conf was the config file for the old gdm version???) "overwrites" the settings from gdm.schema ... both files manage the technical part ... gdm-simple-greeter.schemas is for the "visual" settings???

well ... I wish I could get back my good old gdm :icon_frown:

---

### Post by scradock on 2009-07-05
> **wayne_cat said:**
> From the gdm 2.26 documentation:

```
The GDM daemon is configured using the <etc>/gdm/custom.conf file.  
Default values are stored in GConf in the gdm.schemas file.  It is recommended 
that end-users modify the /etc/gdm/custom.conf file because the schemas file may 
be overwritten when the user updates their system tohave a newer version of GDM.       
```IMHO ... the settings from custom.conf (gdm-custom.conf was the config file for the old gdm version???) "overwrites" the settings from gdm.schema ... both files manage the technical part ... gdm-simple-greeter.schemas is for the "visual" settings???

well ... I wish I could get back my good old gdm :icon_frown:
I guess that's why Ubuntu didn't upgrade from 2.20 for so long - but it beats me why the latest version is so lame, too.

---

### Post by MacUntu on 2009-07-05
Main functionality is there, for the extras: have patience! :)

---

### Post by celticbhoy on 2009-07-05
I seem to have lost my gdm login 'theme' altogether. It shows the same info and login selector, but in a kind of blue/grey scheme with no background image. Not sure what I have done, but in gconf the only entry left under apps/gdm/simple-greeter is the compiz one.

---

### Post by celticbhoy on 2009-07-05
Greeter=/usr/lib/gdm/gdmgreeter

The above is in my /etc/gdm/gdm.conf file, but there is no file of that name in the directory, can someone check if it exists in their's.

---

### Post by wayne_cat on 2009-07-05
> **celticbhoy said:**
> Greeter=/usr/lib/gdm/gdmgreeter

The above is in my /etc/gdm/gdm.conf file, but there is no file of that name in the directory, can someone check if it exists in their's.

the new gdm version 2.26 does not support themes :(

the file gdm.conf is from the old gdm version ... "leftover" ...

---

### Post by celticbhoy on 2009-07-05
There must be something, previously it was the brownish Ubuntu look as shown by everyone here, but now it is blue/grey. Not the background that is a plain grey colour, but the login box window decoration is light blue/grey.

---

### Post by meeples on 2009-07-05
is there no way to get the new gdm to use a gtk theme?

that would be great for seamless gdm -> desktop...

---

### Post by wayne_cat on 2009-07-05
> **meeples said:**
> is there no way to get the new gdm to use a gtk theme?

that would be great for seamless gdm -> desktop...

the old version followed an option in /etc/gdm/gdm.conf

GtkTheme=Human

But this function is not available at the moment.

You can change the background image and the two icons in gdm (the computer icon above the hostname and the user icon) ... sorry :(

---

### Post by wayne_cat on 2009-07-05
> **celticbhoy said:**
> There must be something, previously it was the brownish Ubuntu look as shown by everyone here, but now it is blue/grey. Not the background that is a plain grey colour, but the login box window decoration is light blue/grey.

have you changed something in:

/etc/gdm/custom.conf
/etc/gdm/gdm.schemas

---

### Post by scradock on 2009-07-05
> **wayne_cat said:**
> From the gdm 2.26 documentation:

```
The GDM daemon is configured using the <etc>/gdm/custom.conf file.  
Default values are stored in GConf in the gdm.schemas file.  It is recommended 
that end-users modify the /etc/gdm/custom.conf file because the schemas file may 
be overwritten when the user updates their system tohave a newer version of GDM.       
```IMHO ... the settings from custom.conf (gdm-custom.conf was the config file for the old gdm version???) "overwrites" the settings from gdm.schema ... both files manage the technical part ... gdm-simple-greeter.schemas is for the "visual" settings???

well ... I wish I could get back my good old gdm :icon_frown:
Well, that sounds even more complicated, so I checked a few things out....

1) The "old" conf files (gdm.conf and gdm.conf-custom) are irrelevant, and can be removed without altering behavior.

2) The "new" conf file (custom.conf) also seems to be irrelevant - if I remove it the greeter works fine, as expected. If I put it back, with different settings, they are ignored.

3) The ONLY configuration seems to be done by /etc/gdm/gdm.schemas, plus the visual stuff that is set in /usr/share/gconf/schemas/gdm-simple-greeter.schemas. The ONLY behavior that I can modify is to set TimedLogin and AutomaticLogin (enable/disable) and the user, plus the delay for Time. Even setting Default Welcome on/off doesn't work, though you can set a Banner text (under the Welcome) in gconf.

4) I have no idea when/how/why any changes we make in custom.conf are written to gdm.schemas - so far I have seen no sign that this happens at all.

Hope that helps - let me know if you find a way to actually use custom.conf to make changes......

---

### Post by wayne_cat on 2009-07-05
Let's wait for an answer to this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395861](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395861) 

BTW ... from the wonderful Fedora world:

[https://bugzilla.redhat.com/show_bug.cgi?id=452528](https://bugzilla.redhat.com/show_bug.cgi?id=452528)

---

### Post by celticbhoy on 2009-07-05
wayne_cat could you post your files as mentioned and i can compare with my own

---

### Post by wayne_cat on 2009-07-05
> **celticbhoy said:**
> wayne_cat could you post your files as mentioned and i can compare with my own

the attached files:

```
/etc/gdm/custom.conf

/etc/gdm/gdm.schemas

/usr/share/gconf/schemas/gdm-simple-greeter.schemas

```


had to add ".txt" to the filenames to upload them

---

### Post by celticbhoy on 2009-07-05
cheers - will check them out when i get a chance.

---

### Post by wayne_cat on 2009-07-05
try

```
sudo apt-get remove --purge gdm
sudo apt-get install gdm
```if you can't find an error

---

### Post by celticbhoy on 2009-07-05
will give it a go - did try a re-install with synaptic, but no joy.

---

### Post by scradock on 2009-07-05
> **wayne_cat said:**
> Let's wait for an answer to this bug report:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395861](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395861) 

BTW ... from the wonderful Fedora world:

[https://bugzilla.redhat.com/show_bug.cgi?id=452528](https://bugzilla.redhat.com/show_bug.cgi?id=452528)
Yes, I confirm this - neither custom.conf nor gdm.conf-custom is needed, but if the gdm.conf-custom is there its settings over-ride those in gdm.schemas. Settings in custom.conf don't, contrary to the documentation.

I have confirmed Hernando Torque's bug #395861.....

---

### Post by scradock on 2009-07-05
> **wayne_cat said:**
> try

```
sudo apt-get remove --purge gdm
sudo apt-get install gdm
```if you can't find an error
but make sure you are running in a true console, not under X! Trying to install the new gdm with X running gave me a huge problem with corrupted configuration files.....

---

### Post by Starks on 2009-07-05
Man, I really need to get my Arc-Wise GDM theme working again.

---

### Post by wayne_cat on 2009-07-05
> **scradock said:**
> Yes, I confirm this - neither custom.conf nor gdm.conf-custom is needed, but if the gdm.conf-custom is there its settings over-ride those in gdm.schemas. Settings in custom.conf don't, contrary to the documentation.

I have confirmed Hernando Torque's bug #395861.....

confirmed and subscribed

---

### Post by wayne_cat on 2009-07-05
> **Starks said:**
> Man, I really need to get my Arc-Wise GDM theme working again.

no gdm greeter themes with gdm 2.26 (at the moment)

[http://www.nabble.com/GDM-2.26-themes-vs-earlier-GDM-themes-td23302171.html](http://www.nabble.com/GDM-2.26-themes-vs-earlier-GDM-themes-td23302171.html)

---

### Post by autocrosser on 2009-07-05
OK--the next bit---I've joined the gdm-list & have sent a post to it:
> Greetings..

Ubuntu has now moved to the "new" gdm with Alpha2--there have been several problems with the change-over (I will not go into them here--bug reports have been filed), but many of the testing users are trying to come to grips with the lack of configuration that the new gdm has. I have seen reports from several sources about Gnome developers & the various Distro reps talking & agreeing that the re-write "as-it is" is OK--did anyone take a sample of users? What we see is a large regression that removes choices--I was under the impression that Linux was all about choice.

I find now that I must go in and edit different conf files to try to recover a small fraction of function that the old gdm had--I realize that manpower being what it is--writing a settings panel would take time that "could" be used in other ways, but is there a chance that someone could write a very basic panel to at least cover the schema data?
Come-on everyone---lets get together & if enough voices are raised--we stand a better chance of action.

A very easy way to post is with Nabble--you would need to join the gdm-list & Nabble also...at least join the gdm-list..........lets get some action on this.

---

### Post by autocrosser on 2009-07-05
Thank you for adding wayne_cat!!!!

---

### Post by wayne_cat on 2009-07-05
> **autocrosser said:**
> OK--the next bit---I've joined the gdm-list & have sent a post to it:

Come-on everyone---lets get together & if enough voices are raised--we stand a better chance of action.

A very easy way to post is with Nabble--you would need to join the gdm-list & Nabble also...at least join the gdm-list..........lets get some action on this.

done ... used Nabble to answer ... not  sure if this sends a mail to the mailing list subscribers ;)

BTW .... many thanks

---

### Post by autocrosser on 2009-07-05
> **wayne_cat said:**
> done ... used Nabble to answer ... not  sure if this sends a mail to the mailing list subscribers ;)

BTW .... many thanks

Yes--if you are on the gdm-list it will post it there for you also--very handy.....

---

### Post by scradock on 2009-07-05
> **autocrosser said:**
> Yes--if you are on the gdm-list it will post it there for you also--very handy.....
I've joined and put in my $0.02 worth - hope that helps.....

---

### Post by autocrosser on 2009-07-05
> **scradock said:**
> I've joined and put in my $0.02 worth - hope that helps.....

The more--the better--everyone remember to keep it even-toned & to the point---anyone want to work with slashdot or linux.com? I would think that would raise the dialog a few points:p.......

---

### Post by wayne_cat on 2009-07-05
got a mail from nabble

```
your mail to 'gdm-list' with the subject

    Re: [gdm-list] Is there a timeline for GDMsetup?

Is being held until the list moderator can review it for approval.

The reason it is being held:

    Post by non-member to a members-only list

Either the message will get posted to the list, or you will receive
notification of the moderator's decision.  If you would like to cancel
this posting, please visit the following URL:
```Nabble is good to read the list ... but using the mailing list

```
http://mail.gnome.org/mailman/listinfo/gdm-list
```is the better way to post.

---

### Post by autocrosser on 2009-07-05
Hmmm--I guess that I've been on that list long enough to have things just posted...didn't get one of those in my inbox.......

---

### Post by scradock on 2009-07-05
> **wayne_cat said:**
> got a mail from nabble

```
your mail to 'gdm-list' with the subject

    Re: [gdm-list] Is there a timeline for GDMsetup?

Is being held until the list moderator can review it for approval.

The reason it is being held:

    Post by non-member to a members-only list

Either the message will get posted to the list, or you will receive
notification of the moderator's decision.  If you would like to cancel
this posting, please visit the following URL:
```Nabble is good to read the list ... but using the mailing list

```
http://mail.gnome.org/mailman/listinfo/gdm-list
```is the better way to post.
Hmmm - I joined both the gdm-list and Nabble,just for good luck. I did post through nabble, replying to autocrosser. And I didn't get held back, AFAIK.....

---

### Post by wayne_cat on 2009-07-05
> **scradock said:**
> Hmmm - I joined both the gdm-list and Nabble,just for good luck. I did post through nabble, replying to autocrosser. And I didn't get held back, AFAIK.....

My message is the "Message not available":

[http://mail.gnome.org/archives/gdm-list/2009-July/thread.html](http://mail.gnome.org/archives/gdm-list/2009-July/thread.html)

Your mail arrived ... well ... it's  04.45 in the morning here ... I will have a look at this  after a little map

---

### Post by ronacc on 2009-07-06
> **wayne_cat said:**
>  

BTW ... from the wonderful Fedora world:

[https://bugzilla.redhat.com/show_bug.cgi?id=452528](https://bugzilla.redhat.com/show_bug.cgi?id=452528)

some of the comments in that bug report sound familiar :lolflag:

---

### Post by hgergo on 2009-07-06
hmm gdm still kick me out of the sesion and i must relog.
And with kernel 2.6.31 i have sob problem some colored verikal bars are apering and cant log in

---

### Post by Yes_It's_Me on 2009-07-06
I don't mean to insult any developers but I must say; The reason why nobody is creating even a simple config tool is because... the new gdm just was not designed very well.

It's the same thing with grub2. Editing that thing is a nightmare.

There, it had to be said.

---

### Post by celticbhoy on 2009-07-06
Thanx wayne_cat & scradock, back to what it was.
On another tangent, is it just my system, or does the mouse pointer show the circle version of the hourglass constantly at the login screen? And without an option to change sessions, you dont have the choice of a failsafe login anymore.

---

### Post by rudenko_ruslan on 2009-07-06
> **celticbhoy said:**
> On another tangent, is it just my system, or does the mouse pointer show the circle version of the hourglass constantly at the login screen?
[http://ubuntuforums.org/showpost.php?p=7561250&postcount=134](http://ubuntuforums.org/showpost.php?p=7561250&postcount=134)

):P

---

### Post by celticbhoy on 2009-07-06
OK should pay attention more in class.

---

### Post by Frantique on 2009-07-06
After purging gdm and reinstalling it now the gdm tries to start, but it stucks on showing the busy wheel mouse pointer and that's all... Nothing else happens, it is not moving forward. 
Anyone else noticed this?

---

### Post by MacUntu on 2009-07-06
There are updates in the bug report about which config file to use: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395861](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395861)

Seems gdm.conf-custom is history and everything should go in custom.conf.

---

### Post by wayne_cat on 2009-07-06
> **celticbhoy said:**
> On another tangent, is it just my system, or does the mouse pointer show the circle version of the hourglass constantly at the login screen?

confirmed ;)
[SIZE=3]
[/SIZE]

---

### Post by wayne_cat on 2009-07-06
> **MacUntu said:**
> There are updates in the bug report about which config file to use: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395861](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395861)

Seems gdm.conf-custom is history and everything should go in custom.conf.

Thank you for the information. If you remove or rename gdm.conf-custom you get an error message in /var/log/gdm/:0-slave.log

```
gdm-simple-slave[4615]: WARNING: Unable to load file '/etc/gdm/gdm.conf-custom': No such file or directory
```This will be no problem for the gdm developers ... I'm sure it will be fixed in the next version.I followed the gdm documentation ... as we can see ... that was a bad idea :biggrin:

---

### Post by rudenko_ruslan on 2009-07-06
[https://launchpad.net/ubuntu/karmic/+source/gdm/2.26.1-0ubuntu3](https://launchpad.net/ubuntu/karmic/+source/gdm/2.26.1-0ubuntu3)

Woohoo :)

---

### Post by celticbhoy on 2009-07-06
When was that posted

---

### Post by rudenko_ruslan on 2009-07-06
> **celticbhoy said:**
> When was that posted
Mon Jul 6 15:19:08 BST 2009

[From there]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-July/000586.html").

---

### Post by MacUntu on 2009-07-06
Got the mail 14:25 UTC.

---

### Post by celticbhoy on 2009-07-06
Thanx - just want to know how long to wait.

---

### Post by tjeremiah on 2009-07-06
> **MacUntu said:**
> Martin Pitt on the ubuntu-devel-announce mailing list:

thanks for the heads up.

---

### Post by eris23 on 2009-07-06
What if there are no text consoles?  They've disappeared.

---

### Post by wayne_cat on 2009-07-06
> **eris23 said:**
> What if there are no text consoles?  They've disappeared.

what happens if you press ctrl+alt+F1?

---

### Post by eris23 on 2009-07-06
blinking cursor

---

### Post by tjeremiah on 2009-07-06
so the best thing to do is to wait 2hrs for an update??

---

### Post by wayne_cat on 2009-07-06
> **tjeremiah said:**
> so the best thing to do is to wait 2hrs for an update??

the time is right if:

```
sudo apt-get update
apt-cache show gdm|grep Version | head -n 1
```shows 

```
Version: 2.26.1-0ubuntu3
```

---

### Post by dinxter on 2009-07-06
download new built 2.26.1-0ubuntu3 packages here if cant wait for repository
 [https://launchpad.net/ubuntu/+source/gdm/2.26.1-0ubuntu3](https://launchpad.net/ubuntu/+source/gdm/2.26.1-0ubuntu3)

---

### Post by tad1073 on 2009-07-06
got an error with the .deb:

```
dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor

```

---

### Post by zaomaster on 2009-07-06
> **wayne_cat said:**
> what happens if you press ctrl+alt+F1?

When I press ctrl+alt+F(fill in the number) all I get is a screen full of horizontal colored bars... :(

---

### Post by cb951303 on 2009-07-06
I wish GDM would take its GTK theme preferences from the latest user that logged in. Or at least there was a setting where you could link GDM GTK preferences to a user's GTK theme.

---

### Post by MacUntu on 2009-07-06
> **tad1073 said:**
> got an error with the .deb:

```
dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor

```

Try to install it via the console:```
sudo dpkg -i whatever.deb
```

---

### Post by omgbots on 2009-07-06
> **tad1073 said:**
> got an error with the .deb:

```
dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor

```

I think this is a known issue if you use gdebi.  Try downloading the package and using 'dpkg -i'.

---

### Post by wayne_cat on 2009-07-06
> **zaomaster said:**
> When I press ctrl+alt+F(fill in the number) all I get is a screen full of horizontal colored bars... :(

I have this problem with all kernels > 2.6.30-9-generic. Try to boot one of the other kernel versions (if you haven't removed them).

---

### Post by tad1073 on 2009-07-06
> **zaomaster said:**
> When I press ctrl+alt+F(fill in the number) all I get is a screen full of horizontal colored bars... :(

I am getting the same problem now, I check not 5 min. ago and it was fine.

---

### Post by plun on 2009-07-06
> **MacUntu said:**
> Martin Pitt on the ubuntu-devel-announce mailing list:

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-July/000586.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-July/000586.html)

I  reported this message (mod)  for a sticky thread.

Must be one...

---

### Post by tad1073 on 2009-07-06
got it installed but am still having tha same issues as with the older version.

Have to enter password twice, that metacity dialog box pops-up

---

### Post by tjeremiah on 2009-07-06
> **wayne_cat said:**
> the time is right if:

```
sudo apt-get update
apt-cache show gdm|grep Version | head -n 1
```shows 

```
Version: 2.26.1-0ubuntu3
```

i did the correct input and it saids 2.26.1 -0ubuntu

---

### Post by wayne_cat on 2009-07-06
> **tad1073 said:**
> got it installed but am still having tha same issues as with the older version.

Have to enter password twice, that metacity dialog box pops-up

[http://ubuntuforums.org/showpost.php?p=7570116&postcount=287](http://ubuntuforums.org/showpost.php?p=7570116&postcount=287)

 ```
I just uploaded 2.26.1-0ubuntu3 which should fix the nasty ones, 
the only major one left is the "Doesnot support session saving" dialog
 ([https://launchpad.net/bugs/395324](https://launchpad.net/bugs/395324)), which I'm going to address next.

```and the password problem ... maybe related to pam?

---

### Post by wayne_cat on 2009-07-06
> **tjeremiah said:**
> i did the correct input and it saids 2.26.1 -0ubuntu

that means ... the latest version is still not in the repository ... so you have to wait ;)

---

### Post by tjeremiah on 2009-07-06
> **wayne_cat said:**
> that means ... the latest version is still not in the repository ... so you have to wait ;)

okay.:mad:

---

### Post by tad1073 on 2009-07-06
> **wayne_cat said:**
> [http://ubuntuforums.org/showpost.php?p=7570116&postcount=287](http://ubuntuforums.org/showpost.php?p=7570116&postcount=287)

 ```
I just uploaded 2.26.1-0ubuntu3 which should fix the nasty ones, 
the only major one left is the "Doesnot support session saving" dialog
 ([https://launchpad.net/bugs/395324](https://launchpad.net/bugs/395324)), which I'm going to address next.

```and the password problem ... maybe related to pam?

how can I fix password issue?

---

### Post by zika on 2009-07-06
> **tad1073 said:**
> got it installed but am still having tha same issues as with the older version.
Have to enter password twice, that metacity dialog box pops-upI use AutoLogin (in /etc/gdm/gdm.conf-custom and have moved metacity.desktop from /usr/share/gdm/autostart/LoginWindow to some safe place and put it back later (I don't know why but after some time I've put it back to check if the problem persists and it did not make any problem Yes, I was careful about permissions ...) ...  It works like it did always but better and faster ... :)
update: disregard first part about AutoLogin since gdm ...ubuntu3 made finally gdm.conf-custom obsolete ... I will have to find a place for those two lines in custom.conf ... :)

---

### Post by wayne_cat on 2009-07-06
> **tad1073 said:**
> how can I fix password issue?

any errors in:

```
~/.xsession-errors
```or in:

```
/var/log/auth.log
```

---

### Post by tad1073 on 2009-07-06
> **wayne_cat said:**
> any errors in:

```
~/.xsession-errors
```or in:

```
/var/log/auth.log
```

nothing that indicates gdm

---

### Post by philinux on 2009-07-06
From Martin Pitt just inHello Karmic users,

last Wednesday the new gdm 2.26 landed in Karmic and has caused quite
a bunch of regressions and errors. I just uploaded 2.26.1-0ubuntu3
which should fix the nasty ones, the only major one left is the "Does
not support session saving" dialog ([https://launchpad.net/bugs/395324](https://launchpad.net/bugs/395324)),
which I'm going to address next.

One major bug in the first 2.26 packages was that the package scripts
restarted gdm during the upgrade ([https://launchpad.net/bugs/395302](https://launchpad.net/bugs/395302)).
The package scripts got fixed in 2.26.1-0ubuntu3, so that _from this
version on_ further upgrades will go smoothly. Upgrades from 2.20 (i.
e. Jaunty or Karmic Alpha 2) will also work.

But if you upgraded to gdm 2.26 since last Friday, updating your
system under GNOME will kill the upgrade and your session in the
middle of the update again, since there is no way for the fixed gdm
version to override the previous version's prerm script.

Please follow these steps:

 1. Check your gdm version:

      dpkg -l gdm

    If this says "2.20...", you are fine and can ignore this email.

  2. Do

       sudo apt-get update
       apt-cache show gdm|grep Version:|head -n 1

     If the second command says "2.26.1-0ubuntu3", continue;
     otherwise, wait for an hour. The version should be available on
     archive.ubuntu.com at 1600 UTC today, and a bit later on your
     mirror.

  3. Log out from your X session, to get back to the login manager.

  4. Press Control-Alt-F1 to get to a text console, and log in with
     your normal username/password.

  5. Run an upgrade:

       sudo apt-get dist-upgrade

  6. Press Ctrl+Alt+F7 to get back to the graphical login manager.

Thank you and sorry for the inconvenience,

Martin

-- Martin Pitt | [http://www.piware.de](http://www.piware.de) Ubuntu Developer ([www.ubuntu.com](www.ubuntu.com)) | Debian Developer ([www.debian.org](www.debian.org))

---

### Post by bekind2thenoob on 2009-07-06
> **cb951303 said:**
> I wish GDM would take its GTK theme preferences from the latest user that logged in. Or at least there was a setting where you could link GDM GTK preferences to a user's GTK theme.

Given the nature of the new gdms interface being able to set a gtk theme and backgorund (if not alter the lay out) would be nice

---

### Post by rudenko_ruslan on 2009-07-06
Updated successfully.

The problem with sudden logout is still here :(

---

### Post by pferraro on 2009-07-06
> **rudenko_ruslan said:**
> The problem with sudden logout is still here :(

Has anyone filed a bug for this issue?

---

### Post by celticbhoy on 2009-07-06
Double bonus - my compiz works again.

No still borked.

---

### Post by expensivelesbian on 2009-07-06
follwoing Martin Pitts' steps, I'm still unable to login with my old account. As soon as any of the taskbars turn up, I get booted back out login.

Other users can login. A new user I created can also login. Where should I be looking for what's causing the issue?

---

### Post by jerrylamos on 2009-07-06
> **pferraro said:**
> Has anyone filed a bug for this issue?

See if this one looks familiar:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395595](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395595)

Jerry

---

### Post by JohnJackson on 2009-07-06
> **jerrylamos said:**
> See if this one looks familiar:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395595](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395595)

Jerry

The bug has supposedly been fixed according to that. Can't say that I've experienced any random logouts since upgrading.

---

### Post by rarrue on 2009-07-06
Just in case, in the "local" repositories are not available updates yet.

---

### Post by graaant on 2009-07-06
Yeah, I'm still getting the double login and metacity error too :(

---

### Post by tad1073 on 2009-07-06
Attached is the part of my auth.log that pertains to gmd and logging in.

---

### Post by rarrue on 2009-07-06
I've just updated gdm and still get the double login and error message too. 

Edit: and I've removed the metacity.desktop file.

---

### Post by wayne_cat on 2009-07-06
> **tad1073 said:**
> Attached is the part of my auth.log that pertains to gmd and logging in.

I have seen a problem like this in a german ubuntu forum. The problem was related to eCryptfs. :-k

edit:

did you see this:  PAM unable to dlopen(/lib/security/pam_ecryptfs.so): libecryptfs.so.0: [COLOR=Red]cannot open shared object file: No such file or directory[/COLOR]

---

### Post by wayne_cat on 2009-07-06
> **graaant said:**
> Yeah, I'm still getting the double login and metacity error too :(

See:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395324](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395324)

It will/should be fixed in the next version. 

at the moment .. remove the file:

```
/usr/share/gdm/autostart/LoginWindow/metacity.desktop
```well ... the "double login" problem ... sorry I haven't seen a solution yet :(

---

### Post by celticbhoy on 2009-07-06
On the flip side although removing the metacity file fixes the cant be saved error, it seems to be what causes the perpetually busy mouse pointer.

---

### Post by wayne_cat on 2009-07-06
> **celticbhoy said:**
> On the flip side although removing the metacity file fixes the cant be saved error, it seems to be what causes the perpetually busy mouse pointer.

The error window in gdm has no window decoration until I log on. Maybe gdm tries to load something from a library ... maybe it shows a "I'm waiting for a response from a libray" spinning mouse pointer???

---

### Post by tad1073 on 2009-07-06
> **wayne_cat said:**
> I have seen a problem like this in a german ubuntu forum. The problem was related to eCryptfs. :-k

edit:

did you see this:  PAM unable to dlopen(/lib/security/pam_ecryptfs.so): libecryptfs.so.0: [COLOR=Red]cannot open shared object file: No such file or directory[/COLOR]

yeah, I just looked in /lib/security/ and there is no pam_ecryptfs.so.0 but there is a pam_ecryptfs.so

Maybe it is a type-o in the code? I have no clue.

---

### Post by budluva04 on 2009-07-06
have you tried creating a symlink to .so.0?

---

### Post by wayne_cat on 2009-07-06
> **tad1073 said:**
> yeah, I just looked in /lib/security/ and there is no pam_ecryptfs.so.0 but there is a pam_ecryptfs.so

Maybe it is a type-o in the code? I have no clue.

Do you use eCryptfs?

---

### Post by tad1073 on 2009-07-06
> **wayne_cat said:**
> Do you use eCryptfs?

I don't know if I do or not?  Is it automatic or do I have to invoke it?

---

### Post by wayne_cat on 2009-07-06
> **tad1073 said:**
> I don't know if I do or not?  Is it automatic or do I have to invoke it?

[https://launchpad.net/ecryptfs](https://launchpad.net/ecryptfs)

If you don't use it to encrypt files or /home or whatever ...  apt-get remove it ;)

gdm has a problem with it ...

---

### Post by paul_in_london on 2009-07-06
>   Re: New GDM is uploaded
Quote:
Originally Posted by DougieFresh4U View Post
So I have read through the whole thread.
My question is, through Synaptic upgrade, it wants to remove 'ubuntu-desktop AND gnome-desktop-environment, & gnome
I always thought that I needed one of those desktops in order to have functioning desktop.
wait for a day or two ... you are the first in this thread with this problem. 

On my minimal karmic install, I upgraded to the new gdm successfully by booting into recovery mode first, dropping to a root shell (and accepting the new /etc/gdm/custom.conf when prompted by aptitude). **gnome-desktop-environment** wasn't an issue because it wasn't installed in the first place!

At the moment, though, I still can't upgrade gdm on my "main" karmic install because aptitude wants to remove **gnome-desktop-environment**.

It's been a couple of days since **DougieFresh4U** reported experiencing this issue and (having skimmed through the rest of this thread) no-one else seems have mentioned it since?! :confused:

---

### Post by wayne_cat on 2009-07-06
> **paul_in_london said:**
> On my minimal karmic install, I upgraded to the new gdm successfully by booting into recovery mode first, dropping to a root shell (and accepting the new gdm.conf or whatever it was when prompted by aptitude). **gnome-desktop-environment** wasn't an issue because it wasn't installed in the first place!

At the moment, though, I still can't upgrade gdm on my "main" karmic install because aptitude wants to remove **gnome-desktop-environment**.

It's been a couple of days since **DougieFresh4U** reported experiencing this issue and (having skimmed through the rest of this thread) no-one else seems have mentioned it since?! :confused:

Well ... I'm using gnome and the latest gdm. Is gnome-desktop-environment  superseded?

```
root@macbook:~# dpkg -l |grep gnome-desktop
ii  gnome-desktop-data                             1:2.27.3-0ubuntu1                        Common files for GNOME 2 desktop apps
ii  libgnome-desktop-2-11                          1:2.27.3-0ubuntu1                        Utility library for loading .desktop files -
root@macbook:~# 

```look at the file list:

[http://packages.ubunut.com/karmic/all/gnome-desktop-environment/filelist](http://packages.ubunut.com/karmic/all/gnome-desktop-environment/filelist)

Is it really important?

---

### Post by autocrosser on 2009-07-06
Looks like we are getting some movement towards a settings panel---look at my bugzilla report:  [http://bugzilla.gnome.org/show_bug.cgi?id=587750](http://bugzilla.gnome.org/show_bug.cgi?id=587750)

---

### Post by wayne_cat on 2009-07-06
> **autocrosser said:**
> Looks like we are getting some movement towards a settings panel---look at my bugzilla report:  [http://bugzilla.gnome.org/show_bug.cgi?id=587750](http://bugzilla.gnome.org/show_bug.cgi?id=587750)

It was a good idea to "talk" to Sebastien.

edit: Maybe I should not name him Sabstien

---

### Post by paul_in_london on 2009-07-06
> **wayne_cat said:**
> Well ... I'm using gnome and the latest gdm. Is gnome-desktop-environment  superseded?

```
root@macbook:~# dpkg -l |grep gnome-desktop
ii  gnome-desktop-data                             1:2.27.3-0ubuntu1                        Common files for GNOME 2 desktop apps
ii  libgnome-desktop-2-11                          1:2.27.3-0ubuntu1                        Utility library for loading .desktop files -
root@macbook:~# 

```look at the file list:

[http://packages.ubunut.com/karmic/all/gnome-desktop-environment/filelist](http://packages.ubunut.com/karmic/all/gnome-desktop-environment/filelist)

Is it really important?

Well the short answer appears to be it's not important, but it's late now! :lolflag:

---

### Post by wayne_cat on 2009-07-06
> **paul_in_london said:**
> Well the short answer appears to be it's not important, but it's late now! :lolflag:

Ahh .. saw your name ... also in Europe ... just wait till tomorrow ... other users can have a look at their systems. Is it the only deb that aptitude wants to remove?

---

### Post by paul_in_london on 2009-07-06
> **wayne_cat said:**
> Ahh .. saw your name ... also in Europe ... just wait till tomorrow ... other users can have a look at their systems. Is it the only deb that aptitude wants to remove?

Thanks Wayne. Yeah (apart from fast-user-switch-applet, which is superseded by the new gdm anyway).

Had a quick look at the changelog, which wasn't instantly enlightening. gnome-core *suggests* gnome-desktop-environment, but removing the latter doesn't seem to have screwed anything up so far.

Need to call it a night now!

---

### Post by autocrosser on 2009-07-06
> **wayne_cat said:**
> It was a good idea to "talk" to Sebastien.

edit: Maybe I should not name him Sabstien

I talked with a few people this weekend--I hope that some momentum has been generated--it is very good to hear that the Canonical Desktop team wants to get involved...

I do understand that other distros have been using the new GDM (and I've run across fairly large numbers of bug reports from them too)---but Ubuntu is after all touted as the first move to distro for ex-windows users---so we really need to make the experience as smooth as possible---it simply will not do to have users edit config files to get the functions that they want--most of us here in testing don't have a problem with that..but I have a real problem with apps that have greatly reduced function compared to the prior version.

---

### Post by wayne_cat on 2009-07-07
> **autocrosser said:**
> I talked with a few people this weekend--I hope that some momentum has been generated--it is very good to hear that the Canonical Desktop team wants to get involved...

I do understand that other distros have been using the new GDM (and I've run across fairly large numbers of bug reports from them too)---but Ubuntu is after all touted as the first move to distro for ex-windows users---so we really need to make the experience as smooth as possible---it simply will not do to have users edit config files to get the functions that they want--most of us here in testing don't have a problem with that..but I have a real problem with apps that have greatly reduced function compared to the prior version.

I remember this:

```
[http://live.gnome.org/GDM/NewDesign](http://live.gnome.org/GDM/NewDesign)
```and 

```
[http://ubuntuforums.org/showpost.php?p=7563333&postcount=190](http://ubuntuforums.org/showpost.php?p=7563333&postcount=190)
```I agree with 23meg ... but ... I'm still using the old grub version most of the time... the new version was to complicated for me ... to many problems ... [SIZE=2][COLOR=Black]but [/COLOR][/SIZE][COLOR=Red][SIZE=2][COLOR=Black]I can use the new grub version.[/COLOR][/SIZE][COLOR=Black]

I don't have a dedicated test system ... maybe gdm 2.26 should be an option? ... like the new grub? ... but you can not use the old gdm version ... does not work with the latest Xorg updates :(

I switch between the old and the new grub ... I'm testing ... but I can't switch between the old and the new gdm version .... I'm shipped at the developers mercy.
But maybe gdm is not that important ... the [/COLOR][/COLOR]Canonical Desktop team ...I will accept their
decision ... the next LTS is important ...  and Karmic is a development version. gdm 2.26 does what it should do on my system now ... with a changed background ... changed icons ... changed colors ... but it was a long way ... gdm is "rocket science" ... I learned a lot about the default gnome login window ... more than I wanted ... a lot of people used gdm themes (gone) and the configuration GUI (gone) ... I think they will be disapponted ... gdm 2.26 ... the login screen for Vi users an manual readers.

At least ... Karmic is not boring ;)  
[COLOR=Red][COLOR=Black]



[/COLOR][/COLOR]

---

### Post by scradock on 2009-07-07
> **wayne_cat said:**
> I remember this:

```
[http://live.gnome.org/GDM/NewDesign](http://live.gnome.org/GDM/NewDesign)
```and 

```
[http://ubuntuforums.org/showpost.php?p=7563333&postcount=190](http://ubuntuforums.org/showpost.php?p=7563333&postcount=190)
```I agree with 23meg ... but ... I'm still using the old grub version most of the time... the new version was to complicated for me ... to many problems ... [SIZE=2][COLOR=Black]but [/COLOR][/SIZE][COLOR=Red][SIZE=2][COLOR=Black]I can use the new grub version.[/COLOR][/SIZE][COLOR=Black]

I don't have a dedicated test system ... maybe gdm 2.26 should be an option? ... like the new grub? ... but you can not use the old gdm version ... does not work with the latest Xorg updates :(

I switch between the old and the new grub ... I'm testing ... but I can't switch between the old and the new gdm version .... I'm shipped at the developers mercy.
But maybe gdm is not that important ... the [/COLOR][/COLOR]Canonical Desktop team ...I will accept their
decision ... the next LTS is important ...  and Karmic is a development version. gdm 2.26 does what it should do on my system now ... with a changed background ... changed icons ... changed colors ... but it was a long way ... gdm is "rocket science" ... I learned a lot about the default gnome login window ... more than I wanted ... a lot of people used gdm themes (gone) and the configuration GUI (gone) ... I think they will be disapponted ... gdm 2.26 ... the login screen for Vi users an manual readers.

At least ... Karmic is not boring ;)  
[COLOR=Red][COLOR=Black]



[/COLOR][/COLOR]
Maybe one lesson that needs to be learned, and preferably learned FAST, is that changing which config file is read by default from the one specified in the upstream documentation (custom.conf) just because "GDM has always used gdm.conf-custom" (quote SB) will NOT impress people.

If Canonical/Ubuntu takes the trouble to re-package GNOME packages to fit into a coherent Ubuntu universe the developers MUST either stick to conformity with upstream conventions like that, OR write and publish alternative documentation that addresses Ubuntu-specific conventions.

We did have some fun working it all out over the weekend (didn't we?) but as autocrosser says, it would be absurd to expect regular users to tolerate (let alone enjoy) a similar experience.

---

### Post by scradock on 2009-07-07
> **wayne_cat said:**
> I remember this:

```
[http://live.gnome.org/GDM/NewDesign](http://live.gnome.org/GDM/NewDesign)
```and 

```
[http://ubuntuforums.org/showpost.php?p=7563333&postcount=190](http://ubuntuforums.org/showpost.php?p=7563333&postcount=190)
```I agree with 23meg ... but ... I'm still using the old grub version most of the time... the new version was to complicated for me ... to many problems ... [SIZE=2][COLOR=Black]but [/COLOR][/SIZE][COLOR=Red][SIZE=2][COLOR=Black]I can use the new grub version.[/COLOR][/SIZE][COLOR=Black]

I don't have a dedicated test system ... maybe gdm 2.26 should be an option? ... like the new grub? ... but you can not use the old gdm version ... does not work with the latest Xorg updates :(

I switch between the old and the new grub ... I'm testing ... but I can't switch between the old and the new gdm version .... I'm shipped at the developers mercy.
But maybe gdm is not that important ... the [/COLOR][/COLOR]Canonical Desktop team ...I will accept their
decision ... the next LTS is important ...  and Karmic is a development version. gdm 2.26 does what it should do on my system now ... with a changed background ... changed icons ... changed colors ... but it was a long way ... gdm is "rocket science" ... I learned a lot about the default gnome login window ... more than I wanted ... a lot of people used gdm themes (gone) and the configuration GUI (gone) ... I think they will be disapponted ... gdm 2.26 ... the login screen for Vi users an manual readers.

At least ... Karmic is not boring ;)  
[COLOR=Red][COLOR=Black]



[/COLOR][/COLOR]
wayne_cat - I don't understand what you mean by not being able to switch back? I have two karmic installs, one with the latest greatest GDM (2.26--ubuntu3), the other with the old standard version 2.20 whatever. They both work, they both have the same xserver-xorg-core version (2:1.6.1.901-2ubuntu2). There is no incompatibility with xorg updates as far as I can see, unless you're using some ahead-of-the-curve xorg packages.

In fact, karmic works perfectly fine without gdm at all - simply remove it (from the command line, preferably). Then login at command line, and run startx. You'll be in X, with a complete gnome desktop....

---

### Post by Shopro on 2009-07-07
Today I upgraded 222 packages and it said it was partial upgrade, so I figured it was the kernel upgrade and just went on with it.

After reboot I get stuck with a busy mouse icon in gdm. Been doing some reading and it seems the partial upgrade was in fact the gdm.

So my question is, is there a way to fix the gdm? So far this didn't fix it.

```
sudo apt-get remove --purge gdm
sudo apt-get install gdm
```

EDIT:
After installing gnome-session gdm starts again but if I try to login it just restarts the gdm.

---

### Post by Starks on 2009-07-07
The GDM dropdown in the top-right corner of the panel doesn't theme properly when there is supposed to be a gradient.

[http://img22.imageshack.us/img22/507/lookn.png](http://img22.imageshack.us/img22/507/lookn.png)

---

### Post by zika on 2009-07-07
> **scradock said:**
> In fact, karmic works perfectly fine without gdm at all - simply remove it (from the command line, preferably). Then login at command line, and run startx. You'll be in X, with a complete gnome desktop....If You remove gdm from the loop can You auto-mount USB and other partitions in X ... ? That was the main issue that kept me from leaving it like that in previous incarnations of Ubuntu ...
update: these problems still exist. Some of them are even worse. If I mount CD I can not get it out without reboot. Problem with permissions. Too much problems for a minute gain ... :)

---

### Post by plun on 2009-07-07
New version uploaded:

> **gdm (2.26.1-0ubuntu4)** karmic; urgency=low

  * debian/gdm.preinst: Do not check for an existing custom.conf, since we
    already ship it. Always let the gdm.conf-custom win, to actually migrate
    settings.
  * debian/control: Drop alternative dependencies for gnome-session, since gdm
    itself now needs gnome-session. (LP: #396321).

[https://lists.ubuntu.com/archives/karmic-changes/2009-July/003699.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/003699.html)



---

### Post by Frantique on 2009-07-07
> **plun said:**
> New version uploaded:

Still it does not start to me... I tried to remove it totally, erasing all the directories what gdm created and reinstalling it, but still I see just the busy wheel icon and nothing else. Kdm works, through...

---

### Post by tad1073 on 2009-07-07
> **wayne_cat said:**
>  Karmic is a development version. gdm 2.26 does what it should do on my system now ... with a changed background ... changed icons ... changed colors ... but it was a long way ... gdm is "rocket science" ... I learned a lot about the default gnome login window ... more than I wanted ... a lot of people used gdm themes (gone) and the configuration GUI (gone) ... I think they will be disapponted ... gdm 2.26 ... the login screen for Vi users an manual readers.

At least ... Karmic is not boring ;)  


I just pulled down the gdm update...still has the same effects for me, have to enter password twice, error box pop-up...

I was able to change my background with a work around, naming the picture I want to use to "warty-final-ubuntu.png" but how do I change colors, icon, etc?

I am unable to use gtk window decorator, compiz window decorator works fine, but when I switch to gtk, metacity overrides the gtk window decorator and Iam unable to select window borders from apperence and themes.

---

### Post by celticbhoy on 2009-07-07
To remove the error box goto /usr/share/gdm/autostart/LoginWindow and delete the metacity file.

---

### Post by tad1073 on 2009-07-07
In /usr/share/gdm/ there is a theme folder with themes in it, how do I use those themes with the new gdm?

---

### Post by meeples on 2009-07-07
> **tad1073 said:**
> In /usr/share/gdm/ there is a theme folder with themes in it, how do I use those themes with the new gdm?

i think those are left over from the old gdm, the new one apparently doesnt support themes yet. :(

---

### Post by chrisccoulson on 2009-07-07
The new one can be themed with standard GTK and Metacity themes

---

### Post by tad1073 on 2009-07-07
> **chrisccoulson said:**
> The new one can be themed with standard GTK and Metacity themes

How do I achieve that?

---

### Post by chrisccoulson on 2009-07-07
> **tad1073 said:**
> How do I achieve that?

At the moment with no graphical way of doing this, you can either edit the GConf defaults in gconf-editor, or use "sudo -u gdm gconftool-2 -s --type=<type> <key> <value>" to manually edit the gconf settings for the gdm user.

I don't know of any other way yet.

---

### Post by celticbhoy on 2009-07-07
Where do you get the option to change the theme in gconf-editor??

---

### Post by tad1073 on 2009-07-07
> **celticbhoy said:**
> Where do you get the option to change the theme in gconf-editor??

That,s a good question.

---

### Post by autocrosser on 2009-07-07
I'm putting pressure everywhere I can to get us something that we can change settings with--once the tool is made, I'm sure we can find ways to hack/extend it for more functions---just hang in there--we've got more action in several days--the Fedora users have not got as far in a year.........

---

### Post by damis648 on 2009-07-07
> **tad1073 said:**
> That,s a good question.

Maybe some browsing around in
```
gksudo -u gdm gconf-editor
```
?

---

### Post by scradock on 2009-07-07
> **zika said:**
> If You remove gdm from the loop can You auto-mount USB and other partitions in X ... ? That was the main issue that kept me from leaving it like that in previous incarnations of Ubuntu ...
update: these problems still exist. Some of them are even worse. If I mount CD I can not get it out without reboot. Problem with permissions. Too much problems for a minute gain ... :)
Oh, I'm sure there are very good reasons NOT to run without gdm - I was simply wondering why wayne_cat felt he couldn't use the old one. I haven't actually tried going back, but I do have both versions (2.20 and 2.26) apparently operating correctly in different installs that are otherwise up-to-date.

---

### Post by celticbhoy on 2009-07-07
Can someone tell me if they have access to graphical Users & Groups?

---

### Post by wayne_cat on 2009-07-07
> **chrisccoulson said:**
> The new one can be themed with standard GTK and Metacity themes

True ... so ... let's see what we can do:

_**1. Change the gdm background picture**_

The current settings

```
sudo -u gdm gconftool-2 --get /desktop/gnome/background/picture_filename
```Set a new background picture

```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/background/picture_filename /data/pictures/Grassy.jpg

```_**2. The gdm gtk theme **_

The current settings

```
sudo -u gdm gconftool-2 --get  /desktop/gnome/interface/gtk_theme

```Set a new gtk theme (you can find them in /usr/share/themes)

```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/interface/gtk_theme Redmond
```_**3. The gdm icon theme (changes the look of the computer icon ... icon above the hostname)**_

The current settings

```
sudo -u gdm gconftool-2 --get /desktop/gnome/interface/icon_theme
```Set a new icon theme (You can find them in /usr/share/icons)

```
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/interface/icon_theme Tangerine
```and you can edit the file

```
/usr/share/gconf/schemas/gdm-simple-greeter.schemas
```if you don't like the computer icon. Change the icon (<default>coputer</default>) in the section

```
<schema>
      <key>/schemas/apps/gdm/simple-greeter/logo_icon_name</key>
      <applyto>/apps/gdm/simple-greeter/logo_icon_name</applyto>
      <owner>gdm-simple-greeter</owner>
      <type>string</type>
      <default>computer</default>
      <gettext_domain>gdm</gettext_domain>
      <locale name="C">
        <short>Icon name to use for greeter logo</short>
        <long>Set to the themed icon name to use for the greeter logo.</long>
      </locale>
</schema>
```_**4. The gdm user icon**_

This does not work :(

```
sudo -u gdm gconftool-2 --get /schemas/apps/gdm/simple-greeter/logo_icon_name
```I haven't found it yet ... but at least we could overwrite 
```
/usr/share/icons/gnome/scalable/stock/generic/stock_person.svg 
```but this icon may be important for other applications ... so don't do it. ;)

[COLOR=Red]**solved:** [/COLOR]***[COLOR=Red] you can set the user icon [/COLOR]******[COLOR=Red]for your user[/COLOR]***[I][B][COLOR=Red] with 

[/COLOR][/B][/I]**[COLOR=Red]```
/usr/bin/gnome-about-me
```[/COLOR]**[I][B][COLOR=Red]

[/COLOR][/B][/I]
[I][B]What else can we do???
[COLOR=Red]
edit: added some information about paths (where can i find icon themes ... where can I find gtk themes)

2nd edit: you can change the user icon ... it's so simple 
[/COLOR] [/B][/I]

---

### Post by celticbhoy on 2009-07-07
You can just set the user icon by selecting account info from username at top right

---

### Post by celticbhoy on 2009-07-07
sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/interface/gtk_theme Mac4Lin_GTK_v1.0_RC

Is the above a custom theme location you have ?

---

### Post by wayne_cat on 2009-07-07
> **celticbhoy said:**
> sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/interface/gtk_theme Mac4Lin_GTK_v1.0_RC

Is the above a custom theme location you have ?

Yes ... sorry ... choose a theme name from

```
/usr/share/themes
```

edit:

try this to change the color theme from brown/orange to a blue look

sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/interface/gtk_theme Redmond

---

### Post by wayne_cat on 2009-07-07
> **celticbhoy said:**
> You can just set the user icon by selecting account info from username at top right

thank you ... and if you don't like the icons ... add a new one to:

```
/usr/share/pixmaps/faces/
```

---

### Post by nystire on 2009-07-07
> **JohnJackson said:**
> The bug has supposedly been fixed according to that. Can't say that I've experienced any random logouts since upgrading.

I'm still seeing this bug on my fully updated install.

---

### Post by scradock on 2009-07-07
> **wayne_cat said:**
> thank you ... and if you don't like the icons ... add a new one to:

```
/usr/share/pixmaps/faces/
```
Aren't we having fun?

---

### Post by wayne_cat on 2009-07-07
> **nystire said:**
> I'm still seeing this bug on my fully updated install.

have a look at the gdm log files in

```
/usr/log/gdm
```and the log file

```
/var/log/auth.log
```

---

### Post by wayne_cat on 2009-07-07
> **scradock said:**
> Aren't we having fun?

I'm starting to like gdm 2.26 :lolflag:

---

### Post by nystire on 2009-07-07
Next time it does it, I will. :)

---

### Post by dinxter on 2009-07-07
> **nystire said:**
> I'm still seeing this bug on my fully updated install.

If its [this]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396226") bug, its still in progress but can be worked around with,

           either,
- "sudo stop tty1" after logging into your gnome session
or,
- boot kernel without the splash option to stop it using usplash
 both methods work on this computer

[EDIT] started a thread for gdm random crash bug ease of finding
[http://ubuntuforums.org/showthread.php?t=1206717](http://ubuntuforums.org/showthread.php?t=1206717)

---

### Post by nystire on 2009-07-07
That seems to have fixed it.

---

### Post by JohnJackson on 2009-07-07
> **nystire said:**
> I'm still seeing this bug on my fully updated install.

Yeah, have had it happen once now. Looks like the bug changed to [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396226](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396226)

---

### Post by scradock on 2009-07-07
> **wayne_cat said:**
> I'm starting to like gdm 2.26 :lolflag:
I'm still a bit irritated that each time a new version comes out it resets all the tweaks back to defaults - by over-writing the .schemas. IF we could put tweaks into custom.conf it wouldn't matter (so long as that wasn't also overwritten), but as it is, there are at least three config files to deal with......

---

### Post by autocrosser on 2009-07-07
I copy my tweeked file & name it "name of file.bak" that way I can just do a copy/paste & I'm up again.....

---

### Post by wayne_cat on 2009-07-07
> **scradock said:**
> I'm still a bit irritated that each time a new version comes out it resets all the tweaks back to defaults - by over-writing the .schemas. IF we could put tweaks into custom.conf it wouldn't matter (so long as that wasn't also overwritten), but as it is, there are at least three config files to deal with......


from the gdm 2.26 documenation

```
The GDM daemon is configured using the <etc>/gdm/custom.conf file.  Default
values are stored in GConf in the gdm.schemas file.  It is recommended that 
end-users modify the /etc/gdm/custom.conf file because the schemas file may 
be overwritten when the user updates their system to have a newer version of 
GDM.       
```

---

### Post by scradock on 2009-07-07
> **wayne_cat said:**
> from the gdm 2.26 documenation

```
The GDM daemon is configured using the <etc>/gdm/custom.conf file.  Default
values are stored in GConf in the gdm.schemas file.  It is recommended that 
end-users modify the /etc/gdm/custom.conf file because the schemas file may 
be overwritten when the user updates their system to have a newer version of 
GDM.       
```
Yes - that's true between custom.conf and gdm.schemas; it is actually the gdm-simple-greeter.schemas file that holds the visual tweaks, and that's the one that I would need to back-up before upgrading. Smart move, autocrosser.....

It's also bugging me that the gdm.schemas file in /etc/gdm is NOT a gconf schemas file, while gdm-simple-greeter.schemas, in /usr/share/gconf/schemas, is.

Not only do we have three different files, they follow three different schemes....

---

### Post by scradock on 2009-07-07
> **scradock said:**
> Yes - that's true between custom.conf and gdm.schemas; it is actually the gdm-simple-greeter.schemas file that holds the visual tweaks, and that's the one that I would need to back-up before upgrading. Smart move, autocrosser.....

It's also bugging me that the gdm.schemas file in /etc/gdm is NOT a gconf schemas file, while gdm-simple-greeter.schemas, in /usr/share/gconf/schemas, is.

Not only do we have three different files, they follow three different schemes....
And don't get me started about gconf itself! The gdm program uses the schemas file in /usr/share/gconf/schemas to get its key,value pairs.

The gconf-editor reads its key,value pairs from the gconf database, which only updates from the .schemas files when you run gconf-schemas --register-all, so if the .schemas file is altered (by hand, or by being over-written on upgrade) the values reported by gconf-editor don't reflect the changes. That's what happened this morning - the g-s-m.schemas file was over-written, but the gconf-editor blithely reported the old (tweaked) values, whereas gdm itself read the upgraded (default) values. LAME, LAME, LAME!!!!

---

### Post by hugmenot on 2009-07-07
You guys are doing it wrong.

---

### Post by scradock on 2009-07-07
> **hugmenot said:**
> You guys are doing it wrong.
I'm not sure that helps if an install script chooses to over-write the .schemas file.

---

### Post by hugmenot on 2009-07-07
> **scradock said:**
> I'm not sure that helps if an install script chooses to over-write the .schemas file.

Yes. No idea how gconf works, but I&#8217;ve been using gdm-new for a couple of weeks and no upgrade has deleted my personal greeting message yet.

EDIT: Ya, I tested. No need to touch the schemas at all. Just set to system default.

---

### Post by scradock on 2009-07-07
> **hugmenot said:**
> Yes. No idea how gconf works, but I&#8217;ve been using gdm-new for a couple of weeks and no upgrade has deleted my personal greeting message yet.

EDIT: Ya, I tested. No need to touch the schemas at all. Just set to system default.
I guess you're right, hugmenot. I was trying to see if I could set a file for the icon that wasn't in /usr/share/icons/Human/scalable/devices, but no joy until I set Gnome for my Icon setting in Interfaces AND clicked Set Default.

That's an unhelpful menu item, in my view, because I just Set the value of the key, and Set Default _could_ mean "Oh, I goofed - please put the default value back instead" OR "Make sure that this changed value is marked as the default" OR "Save this changed value somewhere so that if the computer crashes I don't have to re-change it". See what I mean?

Anyway, it does look simpler this way, but I don't know why my tweaks were lost even though they still appeared in gconf-editor!

---

### Post by ranch hand on 2009-07-07
It really does say "Set as Default" not Set Default.  Seems clear to me but I'm the first to admit to misunderstanding a lot of stuff so this may be a fluke.

---

### Post by gwenn on 2009-07-07
Someone tried to use the recovery mode to loggin?

---

### Post by ranch hand on 2009-07-08
With the update for the 7th with 2.6.31-2-16, et al, I am not kicked out of updates before they finish installing into a re-loggin.

Happy.

---

### Post by jerrylamos on 2009-07-08
New gdm -> black screen of death on this Intel i845 video graphics.  Runs for a few minutes then wham!  Black screen, nothing works except power off.  Launchpad bug #396843.

I presume there's no way to back off this level of gdm except by a fresh install of Alpha2 and then being very careful not to update gd(anything)?

Thanks, Jerry

---

### Post by Hairy_Palms on 2009-07-08
ive hacked together a program that lets you set your background image and GTK and icon theme for GDM, it wont work on 64 bit, and its not integrated but it does the job,  hopefully itll inspire someone with more programming talent than me to make something better :D its really just a gui around the gconf commands wayne_cat posted a few pages back


[http://www.megaupload.com/?d=W3ERHPKT](http://www.megaupload.com/?d=W3ERHPKT)

---

### Post by celticbhoy on 2009-07-08
Thnx hairy_palms, if nothing else it will make the time until something is built in more bearable.

---

### Post by zekopeko on 2009-07-08
> **celticbhoy said:**
> Thnx hairy_palms, if nothing else it will make the time until something is built in more bearable.

is there anything being built at all? i don't remember reading anything about the new login window capplet.

---

### Post by celticbhoy on 2009-07-08
If it isn't on the cards yet it will happen at some time. The new gdm has been in Karmic for under a week and look at the length of this thread. Demand and desire will ensure it happens.

---

### Post by wayne_cat on 2009-07-08
> **zekopeko said:**
> is there anything being built at all? i don't remember reading anything about the new login window capplet.

no final decision for gdm2.26 ... at least there is a bug report

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395299](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395299)

gdm 2.26 seems to be a foundation for some new ideas:

[https://wiki.ubuntu.com/DesktopTeam/Specs/GdmFaceBrowser](https://wiki.ubuntu.com/DesktopTeam/Specs/GdmFaceBrowser)

---

### Post by celticbhoy on 2009-07-08
And at the top of the page in the Summary section it states that login should default to face-browser, therefore assuming that it is the default then it stands to reason, that by completion there will be other options.

---

### Post by zekopeko on 2009-07-08
it would be awesome if the ubuntu team would suprise us with the gdm face browser.

---

### Post by Hairy_Palms on 2009-07-08
ill try and see if i can add other options to it tomorrow, enabling/disabling the facebrowser should be easy enough at least.

---

### Post by wayne_cat on 2009-07-08
> **zekopeko said:**
> it would be awesome if the ubuntu team would suprise us with the gdm face browser.

I don't think we will see this in karmic:

```
[https://blueprints.launchpad.net/ubuntu/+spec/gdm-face-browser](https://blueprints.launchpad.net/ubuntu/+spec/gdm-face-browser)

Priority: Medium
Implementation: Slow progress                        
```I can only find some mock-ups ... no alpha version ... nothing ... not even a line of code.

It seems that the Ubuntu design team hired some north korean intelligence agents ... we will not see what they really do until they drop the bomb :biggrin:

---

### Post by celticbhoy on 2009-07-08
Thats a pity, as the video mock-up in the link you posted earlier looked really interesting.

---

### Post by plun on 2009-07-09
More bugs fixed or hacked....

> gdm (2.26.1-0ubuntu5) karmic; urgency=low

  * debian/gdm.preinst: Remove obsolete conffiles.
  * debian/gdm.preinst: Migrate autologin settings from gdm.conf (which isn't
    read any more) to custom.conf. (LP: #396459)
  * Add 81_initial_server_on_vt7.patch: Force initial X server to go to tty7
    instead of tty1. This is an Ugly Hack until we have a cleaner solution for
    getty not to tramp over a running X server on vt1. This bandaids the
    immediate problem of the first X server being killed after a few minutes
    due to getty on tty1 timing out. (LP: #396226)

[https://lists.ubuntu.com/archives/karmic-changes/2009-July/003831.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/003831.html)



Just uploaded so it takes an hour or two until its available.

---

### Post by autocrosser on 2009-07-09
Sounds good--I'll get it in a couple of hours--at work right now.....

---

### Post by wayne_cat on 2009-07-09
Installed with the latest update.

I hope they find a solution for the silly metacity.desktop bug ... new gdm version ... stupid file was there again ;)

---

### Post by DanaG on 2009-07-10
Handy hint, copied from my post in another thread (the one about Shiki-colors):

"Actually, it's not all that hard to configure the new GDM; it's just not documented. Here's how to do it: Go to the login screen, then switch to a TTY and run:
DISPLAY=:0 sudo -u gdm xterm (gnome-terminal won't work -- no gconf daemon running.)

Then you can run gconf-editor (and enable the gnome media-keys thingy / volume-control thingy somewhere in /apps/gdm ) -- and you can also run gnome-appearance-properties.

(In fact, I set metacity to run a console on ctrl-shift-F10, and then edited the entry in /etc/passwd to give gdm user a real /bin/bash shell.)"

---

### Post by Hairy_Palms on 2009-07-11
> Handy hint, copied from my post in another thread (the one about Shiki-colors):

"Actually, it's not all that hard to configure the new GDM; it's just not documented. Here's how to do it: Go to the login screen, then switch to a TTY and run:
DISPLAY=:0 sudo -u gdm xterm (gnome-terminal won't work -- no gconf daemon running.)

Then you can run gconf-editor (and enable the gnome media-keys thingy / volume-control thingy somewhere in /apps/gdm ) -- and you can also run gnome-appearance-properties.

(In fact, I set metacity to run a console on ctrl-shift-F10, and then edited the entry in /etc/passwd to give gdm user a real /bin/bash shell.)"

running gconf-editor like that just spits out a bunch of XML errors and presents an empty root gdm folder, despite gconftool working fine.

---

### Post by DanaG on 2009-07-11
Hmm... did you do it with GDM itself sitting at the login screen?  It won't work, otherwise.  If that doesn't work, then manually (from xterm) start 'usr/lib/libgconf2-4/gconfd-2 &' before opening gconf-editor.

---

### Post by stef70 on 2009-07-12
Sorry if that was already mentioned (I have not read the whole 40 pages of messages) but I found a simple way to configure the GDM appearance. 

(1) Start GDM
(2) Become root on the console
(3) Execute: **sudo -u gdm gnome-control-center**
(4) Switch back to the gdm screen (ALT-F7). 
    The control center should be visible.
(5) Configure you background, theme, fonts, ...

---

### Post by celticbhoy on 2009-07-12
Tried that & just got unknown user error.

---

### Post by stef70 on 2009-07-12
That probably means that gdm is not executed by the gdm user.

ps -eF | grep gdm-simple-greater

---

### Post by stef70 on 2009-07-12
I forgot something! You have to set the DISPLAY before running the control center

export DISPLAY=:0.0

---

### Post by ktp on 2009-07-12
> **stef70 said:**
> 
(3) Execute: **sudo -u gdm gnome-control-center**


> **celticbhoy said:**
> Tried that & just got unknown user error.

Did you replace gdm with your user?

---

### Post by celticbhoy on 2009-07-12
No was I meant to?

---

### Post by plun on 2009-07-12
> **stef70 said:**
> I forgot something! You have to set the DISPLAY before running the control center

export DISPLAY=:0.0

Works fine with this command added...Thanks !;)

---

### Post by celticbhoy on 2009-07-12
Thanx - got it now, think I had a typo when I first tried.

---

### Post by plun on 2009-07-13
More fixes and patches mostly from upstream Git.

> **gdm (2.26.1-0ubuntu6)** karmic; urgency=low

  * Add 00git-greeter-session-management.patch: Make the greeter a
    well-behaved session client. Patch taken from upstream git head.
  * Add 00git-use-after-free.patch: Fix crash in xdmcp chooser. Taken from
    upstream git head.
  * debian/control: Add libxklavier-dev build dependency, to get the
    keyboard selector.
  * Add 04_xklavier4.patch: Fix build with libxklavier 4.0. Taken from
    upstream git head.
  * Add 00git-invalid-dmrc-layout.patch: Correctly handle invalid xkb layout
    from ~/.dmrc. Taken from upstream git head.

[https://lists.ubuntu.com/archives/karmic-changes/2009-July/003971.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/003971.html)


---

### Post by tad1073 on 2009-07-13
> **plun said:**
> More fixes and patches mostly from upstream Git.

How long before it hits all the servers?

---

### Post by Craigy90 on 2009-07-13
> **tad1073 said:**
> How long before it hits all the servers?

I'm downloading an update for gdm right now.

---

### Post by rudenko_ruslan on 2009-07-13
No, it didn't help me. But maybe another GDM update - [https://lists.ubuntu.com/archives/karmic-changes/2009-July/003983.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/003983.html) - will solve it.

---

### Post by wayne_cat on 2009-07-13
after two gdm updates today:

- the gdm-simple-greater error message is gone
- but I still have a "spinning cursor" in gdm

---

### Post by plun on 2009-07-13
> **rudenko_ruslan said:**
> No, it didn't help me. But maybe another GDM update - [https://lists.ubuntu.com/archives/karmic-changes/2009-July/003983.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/003983.html) - will solve it.

Nope....:^o

The greeter bug is still "In Progress"....

[https://bugs.launchpad.net/gdm/+bug/395324](https://bugs.launchpad.net/gdm/+bug/395324)

;)

---

### Post by wayne_cat on 2009-07-13
ahh ... sorry ... I have removed metacity ... maybe this is why I don't get the error window

---

### Post by zika on 2009-07-13
After last upgrade I am kicked off at the greeting window (enter username and pass) due to "unable to authenticate user" ... Luckily I managed to switch on AutoLogin ... :) My password works OK in Terminal and elsewhere ...

---

### Post by wayne_cat on 2009-07-13
> **zika said:**
> After last upgrade I am kicked off at the greeting window (enter username and pass) due to "unable to authenticate user" ... Luckily I managed to switch on AutoLogin ... :) My password works OK in Terminal and elsewhere ...

any errors in the gdm log files? .. you can find them in /var/log/gdm

---

### Post by zika on 2009-07-13
> **wayne_cat said:**
> any errors in the gdm log files? .. you can find them in /var/log/gdmFor example:```
gdm-session-worker[3966]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:1 ruser= rhost=  user=zika
```After AutoLogin:```
(gnome-settings-daemon:3956): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3956): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: Failed to read saved session file /var/lib/gdm/.config/metacity/sessions/102d98f741fb5d1fcd12475135516335000000039500003.ms: Failed to open file '/var/lib/gdm/.config/metacity/sessions/102d98f741fb5d1fcd12475135516335000000039500003.ms': No such file or directory
** (process:3962): DEBUG: Greeter session pid=3962 display=:1.0 xauthority=/var/run/gdm/auth-for-gdm-c7WGN9/database
gdm-simple-greeter[3962]: GLib-GObject-CRITICAL: g_param_spec_flags: assertion `G_TYPE_IS_FLAGS (flags_type)' failed
gdm-simple-greeter[3962]: GLib-GObject-CRITICAL: g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

** (ck-history:3971): WARNING **: Unable to parse session removed event: seat-id='Seat1' session-id='Session5' session-type='' s1245014293.285 type=SEAT_ADDED : seat-id='Seat1' seat-kind=0

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
socket(): Address family not supported by protocol
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
gnome-settings-daemon: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
```and```
gdm-session-worker[3067]: pam_limits(gdm-autologin:session): unknown limit item 'rtorio'
gdm-session-worker[3067]: pam_unix(gdm-autologin:session): session opened for user zika by (uid=0)
gdm-session-worker[3067]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
```

---

### Post by celticbhoy on 2009-07-13
I cant update gdm - greyed out.

---

### Post by wayne_cat on 2009-07-13
> **zika said:**
> For example:```
gdm-session-worker[3966]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:1 ruser= rhost=  user=zika
```After AutoLogin:```
(gnome-settings-daemon:3956): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:3956): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: Failed to read saved session file /var/lib/gdm/.config/metacity/sessions/102d98f741fb5d1fcd12475135516335000000039500003.ms: Failed to open file '/var/lib/gdm/.config/metacity/sessions/102d98f741fb5d1fcd12475135516335000000039500003.ms': No such file or directory
** (process:3962): DEBUG: Greeter session pid=3962 display=:1.0 xauthority=/var/run/gdm/auth-for-gdm-c7WGN9/database
gdm-simple-greeter[3962]: GLib-GObject-CRITICAL: g_param_spec_flags: assertion `G_TYPE_IS_FLAGS (flags_type)' failed
gdm-simple-greeter[3962]: GLib-GObject-CRITICAL: g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

** (ck-history:3971): WARNING **: Unable to parse session removed event: seat-id='Seat1' session-id='Session5' session-type='' s1245014293.285 type=SEAT_ADDED : seat-id='Seat1' seat-kind=0

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
socket(): Address family not supported by protocol
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1000021 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!
gnome-settings-daemon: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
```and```
gdm-session-worker[3067]: pam_limits(gdm-autologin:session): unknown limit item 'rtorio'
gdm-session-worker[3067]: pam_unix(gdm-autologin:session): session opened for user zika by (uid=0)
gdm-session-worker[3067]: pam_ck_connector(gdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
```

I'm following this thread since it appeared ... this error is something that I have not seen since the first upgrade to gdm2.26.

  A lot of pam errors and nothing in the lauchpad bug list about this problem :-k

---

### Post by zika on 2009-07-14
Also, I lost the ability to shutdown, restart, suspend and hibernate. Namely, Ctrl-Alt-Del just restarts X and I have to Ctrl-Alt-F1 to restart or shutdown from CLI. Without AutoLogin I would be in trouble ...

---

### Post by Hairy_Palms on 2009-07-14
latest update 2.26.1-0ubuntu7 broke gdm here, it just shows a black screen with a busy cursor, if i drop to a tty kill X and then startx i get into gnome fine, but gdm refues to start, anyone got any ideas? the only thing in /var/log/gdm is this

> gdm-simple-slave[3665]: WARNING: Child process -3707 was already dead.
gdm-simple-slave[3665]: WARNING: Unable to kill D-Bus daemon

---

### Post by plun on 2009-07-17
New big update uploaded but not yet ready, it takes an hour or two

> gdm (2.26.1git20090717-0ubuntu1) karmic; urgency=low

  * Update to latest upstream git head:
    - [B]Make greeter login window be a dock. Fixes metacity complaining about
      session management. (LP: #395324)[/B]
  * Drop patches which are fixed upstream:
    - 00git-greeter-session-management.patch
    - 00git-invalid-dmrc-layout.patch
    - 00git-use-after-free.patch
    - 00git-xklavier4.patch
    - 02_dont_force_us_keyboard.patch
    - 04_polkit1.patch
  * 80_workaround_incorrect_directories.patch: Update to new upstream version.
  * Drop 01_xconfigoptions.patch; these configure variables are not used any
    more in the upstream code, and upstream supplies the X.org -br option by
    default now. Also drop the corresponding configure changes from
    17_update_default_xserver.patch.
  * Apply 15_usplash.patch to debian/gdm.init and drop the patch.
  * 17_update_default_xserver.patch: Update to new upstream version, add
    corresponding configure change, add patch tag header, forward upstream,
    and rename to 02_x_server_location.patch.
  * Drop 99_autoreconf.patch. The only remaining build system change is the
    previous item.
  * Drop 20_xdm-stuff.patch, it's just cruft.
  * Drop debian/Xsession, and change debian/rules to install the upstream one.
  * 01_xrdb_nocpp.patch: Add patch tag header, forward upstream.
  * Rename 80_workaround_incorrect_directories.patch to
    04_fix_external_program_directories.patch and add patch tag header.
  * Rename 81_initial_server_on_vt7.patch to 05_initial_server_on_vt7.patch.
  * debian/rules: Remove /var/gdm (empty and nonstandard) and /var/run (will
    be created at runtime), thanks lintian.
  * debian/copyright: Point to versioned GPL, thanks lintian.
  * debian/gdm.postrm: Use "set -e" to conform to policy.
  * Add debian/xterm.desktop: Reintroduce "failsafe xterm" session.

[https://lists.ubuntu.com/archives/karmic-changes/2009-July/004354.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/004354.html)



---

### Post by aamukahvi on 2009-07-17
> **plun said:**
> New big update uploaded but not yet ready, it takes an hour or two

Downloded deb from builds, doesn't complain anymore :)

---

### Post by tjeremiah on 2009-07-17
> **plun said:**
> New big update uploaded but not yet ready, it takes an hour or two

so far so good. No longer the metacity error on login.

---

### Post by zika on 2009-07-18
What is the real difference between Gnome and xterm options on login screen ...?
What is this sqeeze/sid that is alternative to zika-computer on login screen ... ?

---

### Post by nyarnon on 2009-07-18
> **zika said:**
> After last upgrade I am kicked off at the greeting window (enter username and pass) due to "unable to authenticate user" ... Luckily I managed to switch on AutoLogin ... :) My password works OK in Terminal and elsewhere ...

Check the keyboard settings shown on the bottomline when you have to put in the password. My local is Dutch on a PT keyboard. The upgrade set the keyboard for GDM to US and therefore my pt keyboard gave a wrong password.
After I switched to PT keyboard again all is well.

---

### Post by zika on 2009-07-18
> **nyarnon said:**
> Check the keyboard settings shown on the bottomline when you have to put in the password. My local is Dutch on a PT keyboard. The upgrade set the keyboard for GDM to US and therefore my pt keyboard gave a wrong password.
After I switched to PT keyboard again all is well.Actually, as I wrote in my message, I was always (until one of upgrades) offered alternative kb for Serbia (Cyrillic), now it is US and it is OK. I newer use pass that is not US compatible ... I've noticed that bottom-line menus ... that is the source for my (idiot) questions about Gnome vs. xterm and zika vs. squeeze/sid ...

---

### Post by wayne_cat on 2009-07-18
> **zika said:**
> What is the real difference between Gnome and xterm options on login screen ...?
What is this sqeeze/sid that is alternative to zika-computer on login screen ... ?

menu entry gnome: starts gnome
menu entry xterm: starts a simple xterm terminal

---

### Post by zika on 2009-07-18
> **wayne_cat said:**
> menu entry gnome: starts gnome
menu entry xterm: starts a simple xterm terminalThank You, after problems with that login-screen I was reluctant to test all options offered ... Still remaining is that squeeze/sid, I Google-ed but no answer ...

---

### Post by wayne_cat on 2009-07-18
> **zika said:**
> Thank You, after problems with that login-screen I was reluctant to test all options offered ... Still remaining is that squeeze/sid, I Google-ed but no answer ...

this is a screen shot of my gdm:

[[IMG]http://ubuntu-pics.de/thumb/19164/gdm_screenshot_9N79N2.png[/IMG]]("http://ubuntu-pics.de/bild/19164/gdm_screenshot_9N79N2.png")

do you have an additional chooser? ... where do you see that "squeeze/sid?

---

### Post by DougieFresh4U on 2009-07-18
> **wayne_cat said:**
> 

do you have an additional chooser? ... where do you see that "squeeze/sid?
I'm glad some one else saw that, yesterday when I was having problems, I got that weird login screen, saying 'sqeeze/sid' and it also said some thing else, I think it had 2 other choices. Changed when you put cursor over it.

---

### Post by zika on 2009-07-18
> **DougieFresh4U said:**
> I'm glad some one else saw that, yesterday when I was having problems, I got that weird login screen, saying 'sqeeze/sid' and it also said some thing else, I think it had 2 other choices. Changed when you put cursor over it.That's it ... You are not alone ...

---

### Post by wayne_cat on 2009-07-18
squeeze/sid problem ... maybe this one:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396866](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396866)

edit: btw ... squeeze and sid are debian distributions

---

### Post by wayne_cat on 2009-07-18
All I have to say is ... "Whisky Tango Foxtrot!" :biggrin:

change the line in 

```
/etc/debian_version
```screen shot with the result

[[IMG]http://ubuntu-pics.de/thumb/19167/gdm_screenshot_37SdyG.png[/IMG]]("http://ubuntu-pics.de/bild/19167/gdm_screenshot_37SdyG.png")

---

### Post by zika on 2009-07-18
> **wayne_cat said:**
> edit: btw ... squeeze and sid are debian distributionsI've thought of that but that did not give any answer to the question why ... until Your next message, it makes sense ...

---

### Post by joepotter on 2009-07-18
So when is it expected that the new gdm may be back to half as good as the old one? And what "improvements" are we trying for here? 

Just asking.

---

### Post by wayne_cat on 2009-07-18
> **zika said:**
> I've thought of that but that did not give any answer to the question why ... :)

I agree to this bug report:
 
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396805](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396805)

---

### Post by Craigy90 on 2009-07-20
I just installed from the daily-live cd on another computer, and enabled auto-login during install. Now, when gdm comes up, it tries to auto-login and says "Authentication failure", then returns to the main window where I can login manually.

Is anyone else seeing this?

---

### Post by zika on 2009-07-20
> **Craigy90 said:**
> I just installed from the daily-live cd on another computer, and enabled auto-login during install. Now, when gdm comes up, it tries to auto-login and says "Authentication failure", then returns to the main window where I can login manually.

Is anyone else seeing this?I'm using AutoLogin all the time. Check the file **/etc/gdm/custom.conf** ...
```
~$ cat /etc/gdm/custom.conf
# GDM configuration storage
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=zika

[xdmcp]

[chooser]

[security]

[debug]
~$ 
```

---

### Post by Craigy90 on 2009-07-20
Mine looks like this

```
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=ubuntu
TimedLoginEnable=true
TimedLogin=craig
TimedLoginDelay=10

```

EDIT:

I made it look like yours, and now it works. Thanks! Should I report a bug for it setting it up wrong during the install?

---

### Post by zika on 2009-07-20
> **Craigy90 said:**
> Mine looks like this

```
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=ubuntu
TimedLoginEnable=true
TimedLogin=craig
TimedLoginDelay=10

```EDIT:

I made it look like yours, and now it works. Thanks! Should I report a bug for it setting it up wrong during the install?It's Your choice ...

---

### Post by dino99 on 2009-07-20
AutomaticLogin not encrypted !!!
Seriously, bad thing for security

---

### Post by yanns on 2009-07-20
> **dino99 said:**
> AutomaticLogin not encrypted !!!
Seriously, bad thing for security

Since when is automatic login something secure???

---

### Post by zika on 2009-07-20
> **dino99 said:**
> AutomaticLogin not encrypted !!!
Seriously, bad thing for securityI'm aware of that. Thank You.

---

### Post by taavikko on 2009-07-20
Going fast forward, 2.27-4 is coming through...

```
gdm 2.27.4-0ubuntu1 (Accepted)
To: karmic-changes@lists.ubuntu.com
Message-ID:
       <20090720140513.10964.86506.launchpad@cocoplum.canonical.com>
Content-Type: text/plain; charset="utf-8"

gdm (2.27.4-0ubuntu1) karmic; urgency=low

 * New upstream release:
   - Favor XFree86 Xinerama over Solaris Xinerama on Solaris
   - Make greeter a well behaved session client
   - XDMCP fixes
   - Fix up btmp record handling
   - Handle locales with modifiers better
   - Use better logic with keyboard layout handling
   - Change example PAM file/documentation to demonstrate password-less login
   - Handle usernames from non-utf8 locales
   - Allow dbus introspection for gdm services
   - Show more details authentication error messages in UI
   - Allow uppercase and lowercase booleans in config file
   - Be more consistent with booleans in schemas
   - Use g_timeout_add_seconds to reduce wakeups
   - Make greeter window more clear when user list is disabled
   - Put greeter login window in same ctrl-alt-tab menu as panel
   - Port greeter to PolicyKit 1.0
   - Shave off 1/2 second delay when bringing up greeter
   - OS X portability fixes
   - Look for locales in /usr/lib/locale instead of /usr/share/locale
   - Better handling when two users have the same name
 * Drop 01_xrdb_nocpp.patch, applied upstream.
 * debian/control:
   - use conflicts on the buggy libxklavier version to avoid race upgrade
     leading to a gdm greeter crash
```

---

### Post by amano on 2009-07-20
This is the actual changelog between 2.26 and 2.27.4.

There haven't been any other GDM releases yet within the 2.27 circle.

---

### Post by rudenko_ruslan on 2009-08-07
So now we will have "a setup tool for basic configuration" (finally!), see this - [https://launchpad.net/ubuntu/karmic/+source/gdm/2.27.4-0ubuntu7](https://launchpad.net/ubuntu/karmic/+source/gdm/2.27.4-0ubuntu7) and this [https://wiki.ubuntu.com/Spec/GDMConfigureTool](https://wiki.ubuntu.com/Spec/GDMConfigureTool)

---

### Post by martinpm24 on 2009-08-07
looks nice

---

### Post by tekstr1der on 2009-08-07
> **martinpm24 said:**
> looks nice

Are you referring to the new setup tool? Doesn't work for me. It launches briefly and crashes out with segfault. Lots of errors:

```
:~$ gdmsetup

** (gdmsetup:3876): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:3876): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): Key not found
** (gdmsetup:3876): DEBUG: init delay=30
** (gdmsetup:3876): DEBUG: GdmUserManager: skipping shell /bin/false
** (gdmsetup:3876): DEBUG: GdmUserManager: Found current seat: /org/freedesktop/ConsoleKit/Seat1
** (gdmsetup:3876): DEBUG: GdmUserManager: running 'ck-history --frequent --seat='Seat1' --session-type='''
** (gdmsetup:3876): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:3876): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:3876): DEBUG: adding monitor for '/home/marc/.face'
** (gdmsetup:3876): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:3876): DEBUG: adding monitor for '/home/test/.face'
** (gdmsetup:3876): DEBUG: Getting list of sessions for user 1001
** (gdmsetup:3876): DEBUG: Found 0 sessions for user test
** (gdmsetup:3876): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:3876): DEBUG: Found 1 sessions for user marc
** (gdmsetup:3876): DEBUG: GdmUser: adding session /org/freedesktop/ConsoleKit/Session2
** (gdmsetup:3876): DEBUG: GdmUserManager: sessions changed user=marc num=1
** (gdmsetup:3876): DEBUG: GdmUserManager: added session for user: marc
** (gdmsetup:3876): DEBUG: GdmUserManager: history output: root     1448

** (gdmsetup:3876): DEBUG: GdmUserManager: excluding user 'root'
** (gdmsetup:3876): DEBUG: GdmUserManager: history output: marc     600

** (gdmsetup:3876): DEBUG: GdmUserManager: history output: test     12

** (gdmsetup:3876): DEBUG: GdmUserManager: history output: ntp      2

** (gdmsetup:3876): DEBUG: Creating new user
** (gdmsetup:3876): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:3876): DEBUG: adding monitor for '/home/ntp/.face'
** (gdmsetup:3876): DEBUG: Getting list of sessions for user 112
** (gdmsetup:3876): DEBUG: Found 0 sessions for user ntp
** (gdmsetup:3876): DEBUG: Login freq 1=600 2=12
** (gdmsetup:3876): DEBUG: Login freq 1=2 2=600
** (gdmsetup:3876): DEBUG: Login freq 1=2 2=12

** (gdmsetup:3876): WARNING **: Error calling GetValue('daemon/AutomaticLoginEnable'): Key not found

** (gdmsetup:3876): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:3876): WARNING **: Error calling GetValue('daemon/TimedLogin'): Key not found
** (gdmsetup:3876): DEBUG: init user='(null)' auto=False
Segmentation fault

```

---

### Post by autocrosser on 2009-08-07
Please look at the Launchpad bug report & do a "affects me too" at the top of the page & then maybe add to my new report about the same thing at the bottom---mine won't seg-fault, but it won't unlock either.........

---

### Post by tekstr1der on 2009-08-07
Link to bug report? Seems to be a few of them already. 

autocrosser, are you refering to [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/410475](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/410475) ?

---

### Post by autocrosser on 2009-08-07
Sorry--I should have specified--I'm one of the early reporters & the bug  [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395299](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/395299)  is the one about needing a gdm config panel--Robert Ancell & Martin Pitt are both subscribed to that bug--so you will get to a developer quickly with it.........

---

### Post by pelle.k on 2009-08-07
I've been looking at screenshots at the new gdm, and UI wise, it looks, erhm, boring... :/
It would be nice if they could tidy it up a bit, and not spread things out that much on the bottom panel. Also, a little usage of padding here and there would be nice.

I'll attach a "regular" panel cut out from one of the screenshots in this thread, and a mockup i made. My mockup just aligns things to the left, makes use of a modern gtk look, and uses a little bit of padding, so that buttons doesn't stretch all the way to the top/bottom. Looks much better IMHO, of course.

---

### Post by wayne_cat on 2009-08-07
gdmsetup also dies on my system ... core dump

added my comment to the bug report

```
root@macbook:/var/lib# gdmsetup 

** (gdmsetup:4974): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:4974): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): The name org.gnome.DisplayManager was not provided by any .service files
** (gdmsetup:4974): DEBUG: init delay=30
** (gdmsetup:4974): DEBUG: GdmUserManager: skipping shell /bin/false
** (gdmsetup:4974): DEBUG: GdmUserManager: Found current seat: /org/freedesktop/ConsoleKit/Seat1
** (gdmsetup:4974): DEBUG: GdmUserManager: running 'ck-history --frequent --seat='Seat1' --session-type='''
** (gdmsetup:4974): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:4974): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:4974): DEBUG: adding monitor for '/home/rschmitt/.face'
** (gdmsetup:4974): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:4974): DEBUG: adding monitor for '/home/test/.face'
** (gdmsetup:4974): DEBUG: Getting list of sessions for user 1001
** (gdmsetup:4974): DEBUG: Found 0 sessions for user test
** (gdmsetup:4974): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:4974): DEBUG: Found 1 sessions for user rschmitt
** (gdmsetup:4974): DEBUG: GdmUser: adding session /org/freedesktop/ConsoleKit/Session2
** (gdmsetup:4974): DEBUG: GdmUserManager: sessions changed user=rschmitt num=1
** (gdmsetup:4974): DEBUG: GdmUserManager: added session for user: rschmitt
** (gdmsetup:4974): DEBUG: GdmUserManager: history output: root     7962

** (gdmsetup:4974): DEBUG: GdmUserManager: excluding user 'root'
** (gdmsetup:4974): DEBUG: GdmUserManager: history output: rschmitt 790

** (gdmsetup:4974): DEBUG: GdmUserManager: history output: test     19

** (gdmsetup:4974): DEBUG: GdmUserManager: history output: gdm      13

** (gdmsetup:4974): DEBUG: GdmUserManager: excluding user 'gdm'
** (gdmsetup:4974): DEBUG: GdmUserManager: history output: (null)   1


** (gdmsetup:4974): WARNING **: Unable to parse history: (null)   1

** (gdmsetup:4974): DEBUG: Login freq 1=790 2=19

** (gdmsetup:4974): WARNING **: Error calling GetValue('daemon/AutomaticLoginEnable'): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:4974): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:4974): WARNING **: Error calling GetValue('daemon/TimedLogin'): The name org.gnome.DisplayManager was not provided by any .service files
** (gdmsetup:4974): DEBUG: init user='(null)' auto=False
Segmentation fault (core dumped)
root@macbook:/var/lib# 
```

---

### Post by martinpm24 on 2009-08-08
> **tekstr1der said:**
> Are you referring to the new setup tool? Doesn't work for me. It launches briefly and crashes out with segfault. Lots of errors:

```
:~$ gdmsetup

** (gdmsetup:3876): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:3876): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): Key not found
** (gdmsetup:3876): DEBUG: init delay=30
** (gdmsetup:3876): DEBUG: GdmUserManager: skipping shell /bin/false
** (gdmsetup:3876): DEBUG: GdmUserManager: Found current seat: /org/freedesktop/ConsoleKit/Seat1
** (gdmsetup:3876): DEBUG: GdmUserManager: running 'ck-history --frequent --seat='Seat1' --session-type='''
** (gdmsetup:3876): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:3876): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:3876): DEBUG: adding monitor for '/home/marc/.face'
** (gdmsetup:3876): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:3876): DEBUG: adding monitor for '/home/test/.face'
** (gdmsetup:3876): DEBUG: Getting list of sessions for user 1001
** (gdmsetup:3876): DEBUG: Found 0 sessions for user test
** (gdmsetup:3876): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:3876): DEBUG: Found 1 sessions for user marc
** (gdmsetup:3876): DEBUG: GdmUser: adding session /org/freedesktop/ConsoleKit/Session2
** (gdmsetup:3876): DEBUG: GdmUserManager: sessions changed user=marc num=1
** (gdmsetup:3876): DEBUG: GdmUserManager: added session for user: marc
** (gdmsetup:3876): DEBUG: GdmUserManager: history output: root     1448

** (gdmsetup:3876): DEBUG: GdmUserManager: excluding user 'root'
** (gdmsetup:3876): DEBUG: GdmUserManager: history output: marc     600

** (gdmsetup:3876): DEBUG: GdmUserManager: history output: test     12

** (gdmsetup:3876): DEBUG: GdmUserManager: history output: ntp      2

** (gdmsetup:3876): DEBUG: Creating new user
** (gdmsetup:3876): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:3876): DEBUG: adding monitor for '/home/ntp/.face'
** (gdmsetup:3876): DEBUG: Getting list of sessions for user 112
** (gdmsetup:3876): DEBUG: Found 0 sessions for user ntp
** (gdmsetup:3876): DEBUG: Login freq 1=600 2=12
** (gdmsetup:3876): DEBUG: Login freq 1=2 2=600
** (gdmsetup:3876): DEBUG: Login freq 1=2 2=12

** (gdmsetup:3876): WARNING **: Error calling GetValue('daemon/AutomaticLoginEnable'): Key not found

** (gdmsetup:3876): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:3876): WARNING **: Error calling GetValue('daemon/TimedLogin'): Key not found
** (gdmsetup:3876): DEBUG: init user='(null)' auto=False
Segmentation fault

```

no the pic in the page :p is not working in my machine also.

---

### Post by autocrosser on 2009-08-08
How new are your installs?  I just reinstalled first part of this week & I'm not getting the seg fault...  *****yes--I finally b0rked my trusty Jaunty update install--used it for over 6 months--was trying to get gnome-shell as a "real" session & gnome-power-manager DID NOT like it :) *****

---

### Post by wayne_cat on 2009-08-08
> **autocrosser said:**
> How new are your installs?  I just reinstalled first part of this week & I'm not getting the seg fault...  *****yes--I finally b0rked my trusty Jaunty update install--used it for over 6 months--was trying to get gnome-shell as a "real" session & gnome-power-manager DID NOT like it :) *****

My installation is an "old" Alpha 1 ... I don't want to install it again ... it would take to
much time to remove the "rubbish" from a fresh installed Karmic and configuere all
settings again :D

hmm ... 

```
 ** (gdmsetup:3876): WARNING **: Error calling GetValue('daemon/AutomaticLoginEnable'): Key not found
```
I don't have the file "org.gnome.DisplayManager.service" in /usr/share/dbus-1/system-services/

---

### Post by autocrosser on 2009-08-08
Interesting--I just tried it this morning & it worked--term output:

dean@linux:~/Desktop$ gdmsetup

** (gdmsetup:3139: WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): Key not found
** (gdmsetup:3139: DEBUG: init delay=30
** (gdmsetup:3139: DEBUG: GdmUserManager: skipping shell /bin/false
** (gdmsetup:3139: DEBUG: GdmUserManager: Found current seat: /org/freedesktop/ConsoleKit/Seat1
** (gdmsetup:3139: DEBUG: GdmUserManager: running 'ck-history --frequent --seat='Seat1' --session-type='''
** (gdmsetup:3139: DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:3139: DEBUG: GdmUserManager: user icon changed
** (gdmsetup:3139: DEBUG: adding monitor for '/home/autocrosser/.face'
** (gdmsetup:3139: DEBUG: GdmUserManager: user icon changed
** (gdmsetup:3139: DEBUG: adding monitor for '/home/dean/.face'
** (gdmsetup:3139: DEBUG: Getting list of sessions for user 1001
** (gdmsetup:3139: DEBUG: Found 1 sessions for user dean
** (gdmsetup:3139: DEBUG: GdmUser: adding session /org/freedesktop/ConsoleKit/Session2
** (gdmsetup:3139: DEBUG: GdmUserManager: sessions changed user=dean num=1
** (gdmsetup:3139: DEBUG: GdmUserManager: added session for user: dean
** (gdmsetup:3139: DEBUG: Getting list of sessions for user 1000
** (gdmsetup:3139: DEBUG: Found 0 sessions for user autocrosser
** (gdmsetup:3139: DEBUG: GdmUserManager: history output: root     95

** (gdmsetup:3139: DEBUG: GdmUserManager: excluding user 'root'
** (gdmsetup:3139: DEBUG: GdmUserManager: history output: dean     13

** (gdmsetup:3139: DEBUG: GdmUserManager: history output: autocros 6

** (gdmsetup:3139: DEBUG: GdmUserManager: unable to lookup user 'autocros'
** (gdmsetup:3139: DEBUG: Login freq 1=13 2=0

** (gdmsetup:3139: WARNING **: Error calling GetValue('daemon/AutomaticLoginEnable'): Key not found
** (gdmsetup:3139: DEBUG: init user='dean' auto=True

I noticed that apport had a update--you might update & then recheck....

---

### Post by autocrosser on 2009-08-08
> **wayne_cat said:**
> My installation is an "old" Alpha 1 ... I don't want to install it again ... it would take to
much time to remove the "rubbish" from a fresh installed Karmic and configuere all
settings again :D

I've got it down to a couple of 2 hour sessions--"almost" can do it in my sleep :D  It also pays to have 2 installs--I just move to my second testing install after I reinstall the main & then chroot into the main to reinstall everything--that way I can be installing whilst doing my normal business...I also sync my storage backup of /var/cache/apt/archives weekly, so my downloads are only at most for the prior week.

---

### Post by wayne_cat on 2009-08-08
does not crash after the update ... great

---

### Post by ranch hand on 2009-08-08
I have 3 pairs of 9.10, A1-clean install and A1-upgraded from 9.04, and so on for A2 and A3 (soon A4).

This GDM will not run on any of them, even from terminal.

Bummer.

---

### Post by wayne_cat on 2009-08-08
> **ranch hand said:**
> I have 3 pairs of 9.10, A1-clean install and A1-upgraded from 9.04, and so on for A2 and A3 (soon A4).

This GDM will not run on any of them, even from terminal.

Bummer.

check the gdm log files in

/var/log/gdm

---

### Post by autocrosser on 2009-08-08
Just for grins I name-changed the Jaunty GDM image (I had it because of some design work for Jaunty) to warty-final-ubuntu.png so I could use it for the new GDM---just as root drop it into /user/share/backgrounds & enjoy.....

---

### Post by ranch hand on 2009-08-08
> **wayne_cat said:**
> check the gdm log files in

/var/log/gdm
As far as I can tell the GDM is not even close to all here.
```

gnome-settings-daemon:11406): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: Failed to read saved session file /var/lib/gdm/.config/metacity/sessions/10fd75fd5030f07b3312483946243639500000114000002.ms: Failed to open file '/var/lib/gdm/.config/metacity/sessions/10fd75fd5030f07b3312483946243639500000114000002.ms': No such file or directory

```
This is somewhat misleading.  /var/lib/gdm is blank.

This was reported automaticaly, seems a lot of folks have this problem in both 32 and 64bit.  I had not checked the logs (dumb) but all that was sent.

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/410475](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/410475)

I wonder if this is, somehow related to my having an ATI card.  Geeze, several pages of ATI checks in the logs to look for the right stuff.  Problably doing that while should have been being installed.

I am sure that it will be straight here soon now that  I have everything working about the way I want it anyway.

---

### Post by wayne_cat on 2009-08-09
> **ranch hand said:**
> As far as I can tell the GDM is not even close to all here.
```

gnome-settings-daemon:11406): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Window manager warning: Failed to read saved session file /var/lib/gdm/.config/metacity/sessions/10fd75fd5030f07b3312483946243639500000114000002.ms: Failed to open file '/var/lib/gdm/.config/metacity/sessions/10fd75fd5030f07b3312483946243639500000114000002.ms': No such file or directory

```This is somewhat misleading.  /var/lib/gdm is blank.

This was reported automaticaly, seems a lot of folks have this problem in both 32 and 64bit.  I had not checked the logs (dumb) but all that was sent.

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/410475](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/410475)

I wonder if this is, somehow related to my having an ATI card.  Geeze, several pages of ATI checks in the logs to look for the right stuff.  Problably doing that while should have been being installed.

I am sure that it will be straight here soon now that  I have everything working about the way I want it anyway.

/var/lib/gdm should not be complete empty ... no hidden files/directories there?

```
root@macbook:~# ls -la /var/lib/gdm
total 20
drwxr-x---  4 gdm  gdm  4096 Aug  8 20:28 .
drwxr-xr-x 73 root root 4096 Aug  8 03:35 ..
drwx------  2 gdm  gdm  4096 Aug  8 20:28 .gconf
drwxr-xr-x  2 gdm  gdm  4096 Aug  8 03:35 .gconf.mandatory
-rw-r--r--  1 gdm  gdm   276 Aug  7 18:11 .gconf.path
root@macbook:~# 
```Do you get these error message if you start gdm from a tty?

---

### Post by ranch hand on 2009-08-09
I ran "dpkg --configure -a" this morning and that seemed to have some effect, hard to believe this was funny on 6 fairly different installs.

Still does not work though.  The files are no longer empty so that is great.

Same message though;
```

ker@ubuntu:~$ sudo gdm

** (gdm-binary:3760): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:3760): WARNING **: Could not acquire name; bailing out
ker@ubuntu:~$ 

```

---

### Post by wayne_cat on 2009-08-09
> **ranch hand said:**
> I ran "dpkg --configure -a" this morning and that seemed to have some effect, hard to believe this was funny on 6 fairly different installs.

Still does not work though.  The files are no longer empty so that is great.

Same message though;
```

ker@ubuntu:~$ sudo gdm

** (gdm-binary:3760): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:3760): WARNING **: Could not acquire name; bailing out
ker@ubuntu:~$ 

```

ranch hand,

The latest gdm package has some bugs. Here is the output from a fresh installation:

1. The installation script in the package has a bug

```
root@macbook:/etc/default# apt-get install gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gok
The following NEW packages will be installed:
  gdm
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B/937kB of archives.
After this operation, 7582kB of additional disk space will be used.
Selecting previously deselected package gdm.
(Reading database ... 234872 files and directories currently installed.)
Unpacking gdm (from .../gdm_2.27.4-0ubuntu9_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Setting up gdm (2.27.4-0ubuntu9) ...
Adding group `gdm' (GID 116) ...
Done.
Warning: The home dir /var/lib/gdm you specified already exists.
Adding system user `gdm' (UID 109) ...
Adding new user `gdm' (UID 109) with group `gdm' ...
The home directory `/var/lib/gdm' already exists.  Not copying from `/etc/skel'.
adduser: Warning: The home directory `/var/lib/gdm' does not belong to the user you are currently creating.
usermod: no changes
usermod: no changes
usermod: no changes
 * Reloading GNOME Display Manager configuration...                                                        * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

```can you see the error ... important ... there was no /var/lib/gdm before the installation!

```
The home directory `/var/lib/gdm' already exists.  Not copying from `/etc/skel'.
adduser: Warning: The home directory `/var/lib/gdm' does not belong to the user you are currently creating.
usermod: no changes
```so I installed it again (without removing it first)... with "--reinstall" ... now look at this:
```

root@macbook:/etc/default# apt-get install --reinstall gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 8 not upgraded.
Need to get 0B/937kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 235013 files and directories currently installed.)
Preparing to replace gdm 2.27.4-0ubuntu9 (using .../gdm_2.27.4-0ubuntu9_i386.deb) ...
Unpacking replacement gdm ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Setting up gdm (2.27.4-0ubuntu9) ...
 * Reloading GNOME Display Manager configuration...                                                        * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.

root@macbook:/etc/default# 
```this time ... everything is ok. 



2. But there is also a "uninstall bug". 

If you use the "purge" option to uninstall gdm (purge = remove the also the configuration files/folders) the purge script also fails (I have attached the file)

```
root@macbook:~# dpkg --purge gdm
(Reading database ... 235012 files and directories currently installed.)
Removing gdm ...
Purging configuration files for gdm ...
dpkg: error processing gdm (--purge):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 gdm
root@macbook:~# 

```and again ... we have an error

```
subprocess installed post-removal script returned error exit status 1
```look at the attached purge script ... it should remove some folders **and the gdm user** but this step fails.

```
root@macbook:~# cat /etc/passwd |grep gdm
gdm:x:109:116:Gnome Display Manager:/var/lib/gdm:/bin/false
root@macbook:~# 

```ok ... so we have to do it again

```
root@macbook:~# dpkg --purge gdm
(Reading database ... 234886 files and directories currently installed.)
Removing gdm ...
Purging configuration files for gdm ...
Removing user `gdm' ...
Warning: group `gdm' has no more members.
Done.
root@macbook:~# 
```now we have a "clean" system

```
root@macbook:~# cat /etc/passwd |grep gdm
root@macbook:~# 
```Now ... your job .... could you please try this:

1. remove gdm (2 times)

```
dpkg --purge gdm
dpkg --purge gdm
```2. install gdm ( also 2 times ... but the 2. installation with "--reinstall")

```
apt-get install gdm
apt-get install --reinstall gdm
```Now you should have a clean installation with the correct permissions for all files and folders. Does it work now?

.

---

### Post by ranch hand on 2009-08-09
I need to get to the hardware store and get some stuff.

I will try this later.  Seems to make sense to me and may just work.

Should be fun in any case.  If it works with the clean A3 I will do it to the others as I get to it.

---

### Post by ranch hand on 2009-08-09
So I try;
```

root@ken-desktop:/home/ken# dpkg --purge gdm
dpkg: dependency problems prevent removal of gdm:
 ubuntu-desktop depends on gdm.
 gdm-guest-session depends on gdm (>= 2.20.7-0ubuntu3).
dpkg: error processing gdm (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 gdm

```
twice.  Does not work.

Try;
```

root@ken-desktop:/home/ken# dpkg --force- --purge gdm
dpkg: gdm: dependency problems, but removing anyway as you requested:
 ubuntu-desktop depends on gdm.
 gdm-guest-session depends on gdm (>= 2.20.7-0ubuntu3).
(Reading database ... 108032 files and directories currently installed.)
Removing gdm ...
Purging configuration files for gdm ...
dpkg: error processing gdm (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 gdm

```
twice.  Will not purge.

This is all on my A3 clean install.  It is on 2 partitions with / on sda and /home on sdb.  This is an external SATA enclosure with no raid so I can only boot from sda.

I mention this because with A2 grub2 would work if installed on this drive only if A2 installed on 1 partition on sda.  I don't think this should effect this current opperation but then again I am green as grass (well maybe greener - this is Montana and August = not so green grass).

---

### Post by wayne_cat on 2009-08-09
ranch hand,

ok ... here is the solution.

1. remove ubuntu-desktop and gdm-guest-session (only temporarily)

```
root@macbook:~# apt-get remove ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-desktop
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 57.3kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 235434 files and directories currently installed.)
Removing ubuntu-desktop ...

``````
root@macbook:~# apt-get remove gdm-guest-session
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gdm-guest-session
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 77.8kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 235443 files and directories currently installed.)
Removing gdm-guest-session ...

```I did not have these two packages on my system ... and now try again.
I have tested it ... installed the two packages ... tried to uninstall gdm ...
got the same error ... removed the packages ... tried again ... gdm can
be reinstalled ... just follow the steps from my other post

After the GDM reinstall you can install  gdm-guest-session and ubuntu-desktop again.

BTW ... gdm-guest-session does not work at the moment ... and ubuntu-desktop ...
arghhh ... I hate this package ... to many dependencies that I don't want on my
systems ... so I removed them.

Sorry for the trouble ... I should use a full Karmic for testing ... just an installation
with all standard packages ... misunderstandings like this would not happen.

---

### Post by ranch hand on 2009-08-09
Well I just got back from there.  I installed the ATI kernal.  Made no difference I could find.

As for full installs - I have never been able to enable any destop effects with this card.  I am happy with that, don't boot up to look at silly stuff on desktop.  Usually run 6 work stations and can't see the desktop in any of them.  But I put in the kernal and updated all that showed up in synaptic and the compiz manager, emerald and some other unsupported thing I can't even rember 15 minutes later and have exactly the same setup that I had before.

This is an improvement as I did go to manager and set the "cube" business.  This ususally locks the system up.  It did not do anythiong so I suppose this is an advance.

I think I will go back and try this stuff now.

---

### Post by wayne_cat on 2009-08-09
Before you start ... try this first:

edit the file

```
/var/lib/dpkg/info/gdm.postrm
```and change the line

```
set -e
```to 

```
set -x
```this will give us a little bit more information why the "--purge" does not work

then

```
dpkg --purge gdm
```

---

### Post by ranch hand on 2009-08-09
```

root@ken-desktop:/home/ken# dpkg --purge gdm
(Reading database ... 129036 files and directories currently installed.)
Removing gdm ...
Purging configuration files for gdm ...
dpkg: error processing gdm (--purge):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Errors were encountered while processing:
 gdm

```
```

root@ken-desktop:/home/ken# dpkg --force- --purge gdm
(Reading database ... 128913 files and directories currently installed.)
Removing gdm ...
Purging configuration files for gdm ...
dpkg: error processing gdm (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 gdm

```
Still seems to not be working.

I have another 64bit 9.10 (A2 updated daily) that is still on the normal kernal and only on 1 partition.  I will try that.

Well maybe not.  Better try the stuff in your last post first, didn't see it.  Blind I guess.

---

### Post by wayne_cat on 2009-08-09
the problem on my sytem was ... the script was not able to delete folder /etc/gdm

change the postrm script ... description in 

[http://ubuntuforums.org/showpost.php?p=7759248&postcount=479](http://ubuntuforums.org/showpost.php?p=7759248&postcount=479)

and try it again ... this will tell us the problem

---

### Post by ranch hand on 2009-08-09
Well, that is interesting;
```

root@ken-desktop:/home/ken# dpkg --purge gdm
(Reading database ... 128913 files and directories currently installed.)
Removing gdm ...
Purging configuration files for gdm ...
+ [ purge = purge ]
+ update-rc.d gdm remove
+ rm -f /etc/default/gdm
+ [ -d /etc/gdm ]
+ rmdir --ignore-fail-on-non-empty /etc/gdm/Init /etc/gdm/PreSession /etc/gdm/PostSession /etc/gdm/PostLogin /etc/gdm/Sessions /etc/gdm
+ [ -d /var/lib/gdm ]
+ rm -r /var/lib/gdm
+ [ -d /var/log/gdm ]
+ rm -r /var/log/gdm
+ getent passwd gdm
+ [ -x /usr/sbin/deluser ]
+ deluser --system gdm
Removing user `gdm' ...
Warning: group `gdm' has no more members.
userdel: user gdm is currently logged in
/usr/sbin/deluser: `/usr/sbin/userdel gdm' returned error code 8. Exiting.
+ getent group gdm
+ [ -x /usr/sbin/delgroup ]
+ delgroup --system gdm
/usr/sbin/delgroup: `gdm' still has `gdm' as their primary group!
+ exit 0

```
To check I tried it again and got;
```

root@ken-desktop:/home/ken# dpkg --purge gdm
dpkg: warning: ignoring request to remove gdm which isn't installed.

```
Moving on I;
```

root@ken-desktop:/home/ken# apt-get install gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  uswsusp gok
The following NEW packages will be installed:
  gdm
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/952kB of archives.
After this operation, 7639kB of additional disk space will be used.
Selecting previously deselected package gdm.
(Reading database ... 128898 files and directories currently installed.)
Unpacking gdm (from .../gdm_2.27.4-0ubuntu9_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Setting up gdm (2.27.4-0ubuntu9) ...
 * Reloading GNOME Display Manager configuration...                                                                                                                               * Changes will take effect when all current X sessions have ended.

```
The reinstall command returned the same result.

Reinstalled desktop.

I think I will reboot and see what happend.

---

### Post by wayne_cat on 2009-08-09
ok .. one question ... did you stop gdm before you tried to uninstall it?

---

### Post by ranch hand on 2009-08-09
Click on System->Administration->Login Screen and it crashes.

Terminal gives;
```

ken@ken-desktop:~$ gdm

** (gdm-binary:6104): WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.62" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:6104): WARNING **: Could not acquire name; bailing out
ken@ken-desktop:~$ sudo gdm
[sudo] password for ken: 

** (gdm-binary:6107): WARNING **: Failed to acquire org.gnome.DisplayManager

** (gdm-binary:6107): WARNING **: Could not acquire name; bailing out
ken@ken-desktop:~$ 

```

---

### Post by wayne_cat on 2009-08-09
hmm ... still a permission problem ... I have attached a file ... could you please try this:

- save the file
- rename it to gdm.conf

then run this command:

```
diff gdm.conf /etc/dbus-1/system.d/gdm.conf
```And your second problem ... try to start gdmsetup from a terminal

```
sudo gdmsetup
```

---

### Post by ranch hand on 2009-08-09
> **wayne_cat said:**
> hmm ... still a permission problem ... I have attached a file ... could you please try this:

- save the file
- rename it to gdm.conf

then run this command:

```
diff gdm.conf /etc/dbus-1/system.d/gdm.conf
```And your second problem ... try to start gdmsetup from a terminal

```
sudo gdmsetup
```
```

ken@ken-desktop:~$ sudo gdmsetup

** (gdmsetup:6005): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:6005): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): Key not found
** (gdmsetup:6005): DEBUG: init delay=30
** (gdmsetup:6005): DEBUG: Failed to identify the current session: Unable to lookup session information for process '6005'

** (gdmsetup:6005): WARNING **: Unable to find users: no seat-id found
** (gdmsetup:6005): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:6005): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:6005): DEBUG: adding monitor for '/home/ken/.face'
** (gdmsetup:6005): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:6005): DEBUG: Found 1 sessions for user ken
** (gdmsetup:6005): DEBUG: GdmUserManager: not adding session on other seat: /org/freedesktop/ConsoleKit/Session2

```
I generally use a big hammer, I like nautilus for doing file things.  I changed the old file to gdm.conf.old and then stuck in the new one.  Had a little trouble finding the difference.  That could have been changed at this end although there may have been some complaints about it by some.

---

### Post by wayne_cat on 2009-08-09
- you can start gdmsetup from the command line?
- you can start gdm with "sudo gdm" now"

---

### Post by ranch hand on 2009-08-09
It is stuff like this that makes you wonder if some things aren't just easier to edit by hand.  I have a nice background for my menu.  The menu font color has been changed for ease of viewing (will be revised again to make it even better). Time out has been changed to 100 so I have time to read the menu.  I am the only user.

Everything seems to be working except I can't get to the Login Sreen controls.

Do we really need all these GUIs?

I guess that I am not picky enough.

ken, by the way, is the nickname for Kernal Klink on this version of Kinky Kitten (that is what everyone calls 9.10 isn't it).

---

### Post by wayne_cat on 2009-08-09
- you can start gdmsetup from the command line?
- you can start gdm with "sudo gdm" now?

---

### Post by ranch hand on 2009-08-09
Not really.  The box comes up and stays up but everything is greyed out, you can't unlock it.

---

### Post by wayne_cat on 2009-08-09
> **ranch hand said:**
> Not really.  The box comes up and stays up but everything is greyed out, you can't unlock it.


a bug ... it crashes if you start it as a user ... and it does not unlock if you start it with sudo
(hint: it should not be started with sudo ... Sebastien Bacher mentioned that in the bug report)

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/410475](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/410475)

---

### Post by ranch hand on 2009-08-10
It has been reported from all 6 of my installs.  They are all a little different but on the same hardware (well 2 are on an internal and the other 4 are on an external).

It just does not work on this box.  I bet they fix it before A4 is out.

---

### Post by plun on 2009-08-25
New larger update for GDM

> gdm (2.27.90-0ubuntu1) karmic; urgency=low

  [ Robert Ancell ]
  * New upstream release: (LP: #418426)
    - Autostart polkit-gnome authentication agent.
    - Add screen capture sound effect to screenshot tool.
    - If HOST_NAME_MAX is not available, try _POSIX_HOST_NAME_MAX, then
      default to 256.
    - Add users "nobody4" and "noaccess" to the list of users to filter from
      the Face Browser.
    - Add Solaris logindevperm support.
    - Fix mispelling of XDMCP.
    - Improve documentation.
  * debian/control:
    - Depend on libcanberra-gtk
  * debian/patches/01_default_keyboard_layout_hal.patch:
  * debian/patches/02_x_server_location.patch:
  * debian/patches/03_hide_system_users.patch:
  * debian/patches/04_fix_external_program_directories.patch:
  * debian/patches/08_use_polkit_for_settings.patch:
  * debian/patches/99_autoreconf.patch:
    - Refreshed
  * debian/patches/09_gdmsetup.patch:
    - Set gdmsetup window title and icon
    - Fix crash when have no default users configured

  [ Ted Gould ]
   * Add 12_fusa_name_change.patch: Change the Bonobo activation server name
     of the FUSA applet.
   * debian/rules: Rename the Bonobo activate server description before
     installing it. (LP: #410498)

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/007187.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/007187.html)



---

### Post by Jay_Bee on 2009-08-25
Fast user switch applet is back! I'm very happy about that :D

---

### Post by plun on 2009-08-25
> **Jay_Bee said:**
> Fast user switch applet is back! I'm very happy about that :D

Yep but it crashed for me the first login....maybe we have a bug  ??

---

### Post by tad1073 on 2009-08-25
no crash here but screen has been flickering and flashing when gdm loads up same thing happens going from login to desktop.

---

### Post by Leighman on 2009-08-25
> **tad1073 said:**
> no crash here but screen has been flickering and flashing when gdm loads up same thing happens going from login to desktop.
y0p!

---

### Post by taavikko on 2009-08-25
> **tad1073 said:**
> no crash here but screen has been flickering and flashing when gdm loads up same thing happens going from login to desktop.

That's the xsplash acting up. (either that or kms)
most visible when using custom background for gdm (mine keeps reverting to black)

---

### Post by microbmen on 2009-09-16
How do you enable xserver in the new GDM?  I cant get port 6000 to listen for the life of me.  Where is the configuration for incoming x?

---

### Post by fubarbundy on 2009-09-27
If this has been posted before, my apologies. From the Run dialogue (Alt-F2):

To use Gnome's UI to edit the appearance of the new GDM directly:

```
gksudo -u gdm dbus-launch gnome-appearance-properties
```

To change all other GDM user settings (mostly irrelevant I suspect):

```
gksudo -u gdm dbus-launch gnome-control-center
```

To edit GConf as the GDM user:

```
gksudo -u gdm dbus-launch gconf-editor
```

---

### Post by fubarbundy on 2009-09-27
If you want to get rid of the accessibility icon from the GDM 'taskbar', it's a little more tricky, because someone's made it 'mandatory'. From the Run dialogue (Alt-F2):

```
gksudo gedit /var/lib/gdm/.gconf.mandatory/%gconf-tree.xml
```

Comment out the following section:

```
<dir name="accessibility">
	<dir name="keyboard">
		<entry name="enable" mtime="1253866193" type="bool" value="true"/>
	</dir>
</dir>
```

It should then look like this:

```
<!--dir name="accessibility">
	<dir name="keyboard">
		<entry name="enable" mtime="1253866193" type="bool" value="true"/>
	</dir>
</dir-->
```

In the GDM control centre (see above post), you can then disable the icon from the completely non-intuitive location of Keyboard -> Accessibility by unticking 'Accessibility features can be toggled with keyboard shortcuts' (what usability genius came up with that? :D)

---

### Post by NCLI on 2009-09-27
I've reported a bug to indicate my dissatisfaction with how hard it is to hide the accessibility icon. Please mark it as "Affects me too" if you agree.

[https://bugs.launchpad.net/netbook-remix-launcher/+bug/437747/](https://bugs.launchpad.net/netbook-remix-launcher/+bug/437747/)

---

### Post by cb474 on 2009-10-14
> **NCLI said:**
> I've reported a bug to indicate my dissatisfaction with how hard it is to hide the accessibility icon. Please mark it as "Affects me too" if you agree.

[https://bugs.launchpad.net/netbook-remix-launcher/+bug/437747/](https://bugs.launchpad.net/netbook-remix-launcher/+bug/437747/)

It really would be better to report the bug directly to Gnome. These annoyances aren't just in Ubuntu. It all comes from Gnome.

[https://bugzilla.gnome.org/](https://bugzilla.gnome.org/)

---

### Post by linusr on 2009-10-27
how to revert back to the default GDM theme?

edit 1: got it after reinstalling gdm

---

