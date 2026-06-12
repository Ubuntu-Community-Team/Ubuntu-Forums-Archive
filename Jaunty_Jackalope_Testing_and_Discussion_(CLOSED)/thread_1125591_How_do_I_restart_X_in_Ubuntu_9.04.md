---
title: "How do I restart X in Ubuntu 9.04?"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Newuser1111 on 2009-04-14
Ctrl+Alt+Backspace doesn't do it.

---

### Post by Elfy on 2009-04-14
No it was disabled. It's in the release notes - Known Issues

[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

---

### Post by Tim Sharitt on 2009-04-14
If you would like to re-enable Ctrl-Alt-Backspace, you'll need to disable dontzap.


Add to /etc/X11/xorg.conf

```
Section "ServerFlags"
        Option          "DontZap" "false"
EndSection
```

---

### Post by bennachie on 2009-04-14
You might also like to add your voice to the vast majority of those who have already commented on this issue who would have preferred to see the well-established <ctrl-alt-backspace> key combination raise a cautionary dialogue rather than be disabled altogether. The alternative combination, now apparently preferred by "upstream" developers, is to use the right-hand Alt key, followed by SysRq and K.

---

### Post by randiroo76073 on 2009-04-17
And prey tell where did they come up with a completely goofy idea for that key combo ???

---

### Post by bennachie on 2009-04-17
I've no idea at all, and have seen no rational explanation for the move - it must have seemed a good idea at the time. I suppose that "K" is supposed to indicate that the combination will "kill" the current desktop. I can't believe that hundreds of users were accidentally hitting <ctrl-alt-bksp>.

---

### Post by hyl4me on 2009-04-18
> **randiroo76073 said:**
> And prey tell where did they come up with a completely goofy idea for that key combo ???

In addition, my laptop as well as others don't even work with SysRq because of the Fn key.

---

### Post by Nullack on 2009-04-18
sudo /etc/init.d/gdm stop/start/restart

---

### Post by hikaricore on 2009-04-18
[[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/waste.jpg[/IMG]]("http://ubuntuforums.org/showthread.php?t=1040988")

What a waste of a perfectly good feature, there's no sane reason to accidently hit 3 keys.

---

### Post by Zorael on 2009-04-18
Restarting X that way won't let apps shut down properly (saving data), no? I always log out, then vtswitch and do 'sudo service kdm restart'.

---

### Post by ruffneck on 2009-04-18
> **Tim Sharitt said:**
> If you would like to re-enable Ctrl-Alt-Backspace, you'll need to disable dontzap.


Add to /etc/X11/xorg.conf

```
Section "ServerFlags"
        Option          "DontZap" "false"
EndSection
```

Thanks....this worked.

---

### Post by hikaricore on 2009-04-18
> **Zorael said:**
> Restarting X that way won't let apps shut down properly (saving data), no? I always log out, then vtswitch and do 'sudo service kdm restart'.

Your way does essentially the same thing.  ^_^
Open applications won't shut down properly and you'll lose unsaved data.
I fail to see why this is any better.

---

### Post by scradock on 2009-04-18
In my experience the main reason for needing to use CTL-ALT-BKSPCE is precisely because some open app refuses to close and needs to be killed in brutal fashion. Especially if I'm in a hurry, killing the whole gdm gets me back up and running quickly without having to identify which process to kill.

---

### Post by Zorael on 2009-04-20
> **hikaricore said:**
> Your way does essentially the same thing.  ^_^
Open applications won't shut down properly and you'll lose unsaved data.
I fail to see why this is any better.
I *log out* first. :3

---

### Post by crjackson on 2009-04-20
> **hyl4me said:**
> In addition, my laptop as well as others don't even work with SysRq because of the Fn key.

Ditto, and the fact that mine only has one alt key on the left side of the keyboard.

---

### Post by inportb on 2009-04-20
> **randiroo76073 said:**
> And prey tell where did they come up with a completely goofy idea for that key combo ???

That's the secure access key; it kills all apps running on the current terminal, including X.

---

### Post by ktp on 2009-04-20
> **Zorael said:**
> I *log out* first. :3

You can't always log out when it hangs.

---

### Post by ktp on 2009-04-20
> **randiroo76073 said:**
> And prey tell where did they come up with a completely goofy idea for that key combo ???

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by cornflake000 on 2009-04-21
I did the DontZap thing in xorg a long time ago.  It has never worked.  CTL-ALT-BKSPCE doesn't work in either case for me.  Dumb.  There may be a couple of unusual keyboard layouts, probably laptops, where a couple of people had a problem.  I've never made that mistake or heard of anyone making that mistake.

---

### Post by ELD on 2009-04-21
> **hikaricore said:**
> [[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/waste.jpg[/IMG]]("http://ubuntuforums.org/showthread.php?t=1040988")

What a waste of a perfectly good feature, there's no sane reason to accidently hit 3 keys.

So much for them doing what the users want eh?

---

### Post by Kazade on 2009-04-21
> **bennachie said:**
> I've no idea at all, and have seen no rational explanation for the move - it must have seemed a good idea at the time. I suppose that "K" is supposed to indicate that the combination will "kill" the current desktop. I can't believe that hundreds of users were accidentally hitting <ctrl-alt-bksp>.

I've been using Ubuntu since Breezy so I'm really used to the CTRL+ALT+BKSP key combo, but I have to admit when I first started using Linux I remember I hit that combo a few times before working out what it was. I don't agree it should be completely disabled, I think we should copy Windows on this one, CTRL+ALT+DEL (or BKSP) should bring up a dialog or the system monitor. Or even better, CTRL+ALT+DEL should bring up the system monitor and CTRL+ALT+BKSP should bring up a "Are you sure you want to restart X?" dialog.

EDIT: Hmm.. I totally forgot CTRL+ALT+DEL brings up the restart/shutdown etc. dialog. Couldn't we just add a restart X option to that?

---

### Post by Zorael on 2009-04-21
> **ktp said:**
> You can't always log out when it hangs.
Conceded. That just never happens for me; when I restart X, I do it to reload drivers/configuration. If it hangs, I've gotten a kernel panic, and no amount of zapping will get me out of that.

---

### Post by HankB on 2009-04-21
> **cornflake000 said:**
> ...  I've never made that mistake or **heard of anyone making that mistake**.

<raises hand>

I use <ctrl><alt><left> and <ctrl><alt><right> to switch between desktops. I recall hitting <ctrl><alt><backspace> once or twice by mistake. It's a real eye opener when everything suddenly disappears.

---

### Post by aldeby on 2009-04-21
> **bennachie said:**
> I can't believe that hundreds of users were accidentally hitting <ctrl-alt-bksp>.

I can't believe it either!

It seems to me so incredibly ridiculous that any human being can ever press CTRL+ALT+BKPS *by accident*.

---

### Post by Zorael on 2009-04-21
> **ELD said:**
> So much for them doing what the users want eh?
Noteworthy is that the people that voted in the poll are people who are trying out a per-definition unstable development version of a future release, and not Joe Users.

---

### Post by Simian Man on 2009-04-21
> **aldeby said:**
> I can't believe it either!

It seems to me so incredibly ridiculous that any human being can ever press CTRL+ALT+BKPS *by accident*.

You're forgetting one large group of masochists: Emacs users.  Emacs makes heavy use of Ctrl-Alt key combinations leading to some users accidentally hitting backspace.  I guess a large number of X developers are Emacs users (unlike Ubuntu users).

[quote=bennachie]You might also like to add your voice to the vast majority of those who have already commented on this issue who would have preferred to see the well-established <ctrl-alt-backspace> key combination raise a cautionary dialogue rather than be disabled altogether.[/quote]

And how would a dialogue help if X is non-responsive?

---

### Post by amano on 2009-04-21
> **aldeby said:**
> I can't believe it either!

It seems to me so incredibly ridiculous that any human being can ever press CTRL+ALT+BKPS *by accident*.

Just imagine someone typing an article from a book. If there is only a small computer table, the book might touch the keyboard sometimes. If it does so when correcting a mistake, it will kill your X and the whole article has gone to the heaven of lost literature ;)

BTW, what is so bad about remembering AltGR+SysRQ+K?
It does the same and will hopefully not be harder to remember than the old combo.

---

### Post by Newuser1111 on 2009-04-21
> **amano said:**
> BTW, what is so bad about remembering AltGR+SysRQ+K?Because if your on a laptop then you might have to do AltGR+Fn+PrtSc+K if it would even work.

And I made this thread because I had to restart X because the DE crashed.

---

### Post by amano on 2009-04-21
If that happens to you, just file a bug that PrintScr should kill X as well.

On my laptop AltGR+PrintScr+K does this correctly. If it doesn't for you, filing a bug will certainly help.

---

### Post by Sukarn on 2009-04-21
> **Zorael said:**
> Noteworthy is that the people that voted in the poll are people who are trying out a per-definition unstable development version of a future release, and not Joe Users.

I have voted "no" on that thread a month or two ago because I am against this move. I am not even now on 9.04, but I happen to frequent development version forums and I voted on it.

The problem I have with this move is that too many people are used too the old method which works and involves three such keys which are next to impossible to hit together "by mistake".

Also, my laptop keyboard does not have a right alt key, which effectively makes this new combination very bad for me, like other people here who do not have a SysRq key on their laptop.

---

### Post by Geekkit on 2009-04-21
> **bennachie said:**
> ... who would have preferred to see the well-established <ctrl-alt-backspace> key combination raise a cautionary dialogue rather than be disabled altogether.

This is the perfect solution and yet it apparently was overlooked. Talk about the Ubuntu team having tunnel vision.

---

### Post by Zorael on 2009-04-21
There's also a terminal command, **dontzap** (from the package of the same name) that automates enabling/disabling zapping.

[http://packages.ubuntu.com/jaunty/dontzap](http://packages.ubuntu.com/jaunty/dontzap)

edit:
> **Sukarn said:**
> I have voted "no" on that thread a month or two ago because I am against this move. I am not even now on 9.04, but I happen to frequent development version forums and I voted on it.

The problem I have with this move is that too many people are used too the old method which works and involves three such keys which are next to impossible to hit together "by mistake".

Also, my laptop keyboard does not have a right alt key, which effectively makes this new combination very bad for me, like other people here who do not have a SysRq key on their laptop.
Obviously, barring exceptions. :>

As an anecdote, I have several ctrl+alt+<key> shortcuts for toggling scim and Anthy for Japanese input. I try to stay away from backspace, but hitting it by mistake is not that far an imaginary stretch.

Zapping isn't *removed* as a feature, it's merely opt-in now instead of opt-out.

---

### Post by cornflake000 on 2009-04-21
Maybe I'm repeating myself... well, I am repeating myself...

The dontzap thing does not work for everyone.  I have no choice but to do without at this point.

and to the great literature being lost...  Exactly how many monkeys does it take on how many typewriters and for how long to come up with Shakespeare's Hamlet?  Hmmmm

---

### Post by raymondh on 2009-04-21
> **Tim Sharitt said:**
> If you would like to re-enable Ctrl-Alt-Backspace, you'll need to disable dontzap.


Add to /etc/X11/xorg.conf

```
Section "ServerFlags"
        Option          "DontZap" "false"
EndSection
```

This is my first time to edit xorg so pls. bear with me. 

```
 Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
```

Should I do this as well?  I just want my ctrl+alt+backspace combo back.

Thanks

---

### Post by ktp on 2009-04-21
> **raymondhenson said:**
> This is my first time to edit xorg so pls. bear with me. 

```
 Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
```

Should I do this as well?  I just want my ctrl+alt+backspace combo back.

Thanks

You should only have to change the xorg.conf.  Make sure to reboot to make sure changes are taken.

---

### Post by Sukarn on 2009-04-22
> **raymondhenson said:**
> This is my first time to edit xorg so pls. bear with me. 

```
 Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
```

Should I do this as well?  I just want my ctrl+alt+backspace combo back.

Thanks


yes, you should add the part you quoted into xorg.conf, and then after you save and close the file, you should run the above command in a terminal window so that any future update to xorg would not remove what you added to xorg.conf

---

### Post by raymondh on 2009-04-22
> **Sukarn said:**
> yes, you should add the part you quoted into xorg.conf, and then after you save and close the file, you should run the above command in a terminal window so that any future update to xorg would not remove what you added to xorg.conf

After a simple edit to xorg.conf (mentioned previously) and saving, I successfuly tested by using ctrl+alt+backspace numerous times yesterday and today, specially with misbehaving apps. Then I decide to follow the above-quoted advice....... I now CANNOT boot x and am getting an postinst warning.  Help. Arrrrgggh (kicking myself, kicking myself)

What happens is that about 5 secs into spalsh, my screen goes blank/black and stays that way (26 mins. and counting form the last try).

Booting into recovery mode to try to auto-fix graphics problems, I get this message:

> xserver-xorg postinst warning: overwriting possibly-customized configuration file. back up in /etc/x11/xorg.conf.20090422143028

How can I fix this and get back to normal? Seems that I have to go back to the back-up file but I don't know how.  Help appreciated.

Arrrgggggh.

Raymond

---

### Post by peakshysteria on 2009-04-22
> [How to enable/disable Ctrl+Alt+Backspace from the command line]("http://albertomilone.com/wordpress/?p=335")

If you don’t want to use a user interface to change the effect of Ctrl+Alt+Backspace in any flavour of Ubuntu you can follow these steps:
1) Install the “dontzap” package
sudo apt-get install dontzap
2) Open Terminal or Konsole and type:
sudo dontzap –enable
or
sudo dontzap –disable
Where “disable” means that Ctrl+Alt+Backspace restarts the xserver while “enable” means that it won’t.

I enabled Ctrl+Alt+Backspace after sudo apt-get install dontzap with the command:
```
sudo dontzap --disable
```

---

### Post by Sukarn on 2009-04-22
> **raymondhenson said:**
> After a simple edit to xorg.conf (mentioned previously) and saving, I successfuly tested by using ctrl+alt+backspace numerous times yesterday and today, specially with misbehaving apps. Then I decide to follow the above-quoted advice....... I now CANNOT boot x and am getting an postinst warning.  Help. Arrrrgggh (kicking myself, kicking myself)

What happens is that about 5 secs into spalsh, my screen goes blank/black and stays that way (26 mins. and counting form the last try).

Booting into recovery mode to try to auto-fix graphics problems, I get this message:



How can I fix this and get back to normal? Seems that I have to go back to the back-up file but I don't know how.  Help appreciated.

Arrrgggggh.

Raymond

If you edited using gedit (Text Editor), then it automatically makes a backup file when you press Save.

Go into recovery mode and type **cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup** and then type **cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf**

If you did not use gedit to edit the file, then just go into recovery mode and open the file with **nano /etc/X11/xorg.conf** and remove the changes made earlier. Now press **ctrl+x** followed by **y** and then press **enter**. This will save the file and quit nano (command line text editor).

Now type **dpkg-reconfigure -phigh xserver-xorg** to make your changes permanent.

Type **reboot** to restart the computer and then try the dontzap method.

Lastly, try forgiving me if you think I had any part in the problem you faced on your computer.

---

