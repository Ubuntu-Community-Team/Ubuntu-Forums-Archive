---
title: "crontab issue?"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gnudoc on 2008-10-19
I have an extremely simple script run by cron. It basically takes a random image from my wallpapers directory and makes it the gnome background - cron runs it every 10 minutes. It's attached if anyone's curious.

This was working fine on hardy but doesn't seem to be working so well in intrepid. the script executes perfectly if i run it directly. but, although it runs (i know this because the log file is updated correctly on time every 10minutes), it doesn't actually change the background.

Initially I thought this could be an issue with the last line of the script which uses gconftool, and is the only line that the logging line doesn't rely on. However, the script executes exactly right every time if run directly, and directly running just the gconftool line changes the background to the chosen file without an error message.

So I tried running just gconftool from crontab a moment ago with: ```
24 12 * * * gconftool -t string -s /desktop/gnome/background/picture_filename /home/gnudoc/Pictures/wallpaper/linux/warty-final-ubuntu.png
25 12 * * * gconftool -t string -s /desktop/gnome/background/picture_filename /home/gnudoc/Pictures/wallpaper/linux/Ubuntu-Tropic_1920x1200.png
```

(I don't know if the forum will autowrap that, but obviously each line of crontab was on a single line)

It didn't work. The background stayed resolutely the same each time. :( Yet the exact same command from the command prompt then worked fine a moment later.

Any ideas why gconftool won't execute if run by crontab? Is this a permissions thing? But why wouldn't my crontab have permission to run something that I'm running as me from the command line?

Thanks
gnudoc

---

### Post by mike2357 on 2008-10-19
I'm having the exact same problem, except I'm using gconftool-2 commands as follows:

gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$picture_name"
gconftool-2 -t str --set /desktop/gnome/background/picture_options "stretched"

I added the following to find out if gconfd is even running:
gconftool-2 --ping
echo $?

When run the command line, it shows 0 (running) but from cron it shows 2 (not running).  That would seem to explain why all of the other gconftool-2 commands don't work.

I don't have an answer, but maybe a clue that will help someone else figure this out.

---

### Post by geirha on 2008-10-19
Which crontab are you running these? You must run it in your user's crontab by running ```
crontab -e
``` as your own user. If you run it by doing ```
sudo crontab -e
``` it will try to change root's wallpaper ...

---

### Post by mike2357 on 2008-10-19
I don't think it's an issue with running in the wrong user's cron.  I'm running in my own cron (not root's), and things worked fine in prior Ubuntu versions.  Also, various output messages in my script are executed perfectly.

---

### Post by sparky-steve on 2008-10-19
although it seems unlikely, change your crontab to use the full path to gconftool. it's probably /usr/bin/gconftool

```
which gconftool
```

will tell you the full path

```
24 12 * * * /usr/bin/gconftool -t string -s /desktop/gnome/background/picture_filename /home/gnudoc/Pictures/wallpaper/linux/warty-final-ubuntu.png
```

If it works you'd do the same in your script:

```
#assign the actual wallpaper
/usr/bin/gconftool -t string -s /desktop/gnome/background/picture_filename $file
```

I've had similar issues in previous versions of linux, even though it should be in the default path.

SS

---

### Post by geirha on 2008-10-19
If a command fails with an error message, cron will mail it to you. Type ```
mail
``` in a terminal to read such mails.

---

### Post by mike2357 on 2008-10-19
I inserted /usr/bin/ before gconftool-2.  Still no success. Also, the cron script itself is running.  Thanks for the advice.  As with gnudoc, this worked fine in Hardy but not in Intrepid, which I realize is still in beta.  Possibly a bug that should be reported?

---

### Post by gnudoc on 2008-10-19
Thanks for all the quick replies, guys.

mike2357: thanks for that. nice to see i'm not insane. :)
geirha: yes, i did of course make sure i was using my own crontab, to the extent of doing crontab -u gnudoc -e to double-check.
sparky-steve: didn't think of that, thanks. unfortunately, specifying which gconftool to use in my script hasn't helped either. :(

mkay.  i think since mike2357 is able to confirm this issue, i might have to report this as a bug. unless anyone can suggest what we're missing here in the next couple of hours, i guess i'll go ahead and do that. incidentally, i had a look in lp and couldn't find any bug matching this at the moment.

gnudoc

---

### Post by geirha on 2008-10-19
Try setting the DISPLAY variable. 
```
* * * * * DISPLAY=:0.0 gconftool -t string ...
```

It's a shot in the dark, and I think it would be a silly thing to require a DISPLAY to be specified in order to change wallpaper, but it might be some new feature/bug that has been introduced in later verisons.

---

### Post by gnudoc on 2008-10-19
geirha: nope :(

nice try, thanks.

I've tried that both in my script and directly in a crontab line but no joy.

any other thoughts?

---

### Post by mike2357 on 2008-10-19
I tried the DISPLAY command in my script; still no luck.  Thanks for the suggestions everyone.

I submitted a bug in launchpad.  The bug number is 285937.  Feel free to add to it.

---

### Post by mike2357 on 2008-10-19
Apparently this is not a bug in gconftool-2, but with Intrepid it uses different back-end stuff which I won't pretend to understand.  However, the following solution works with using gconftool-2 in Intrepid in a script called by cron:

1)  Make a file in your home directory that creates a file with environment variables needed by gconftool-2.  I called mine .make_Xdbus and here are the contents:

```
#!/bin/bash
# Export the dbus session address on startup so it can be used by cron
touch $HOME/.Xdbus
chmod 600 $HOME/.Xdbus
env | grep DBUS_SESSION_BUS_ADDRESS > $HOME/.Xdbus
echo 'export DBUS_SESSION_BUS_ADDRESS' >> $HOME/.Xdbus
# Export XAUTHORITY value on startup so it can be used by cron
env | grep XAUTHORITY >> $HOME/.Xdbus
echo 'export XAUTHORITY' >> $HOME/.Xdbus

```

2) Make .make_Xdbus run each time you log in by selecting System -> Preferences -> Sessions and add /home/your_name/.make_Xdbus as a Startup program.  To test, log out and log back in and check to be sure a file called .Xdbus is there.

3) Modify your cron command so it sources .Xdbus before calling the script which contains the call to gconftool-2.  Here's an example from my cronfile:

```
00,10,20,30,40,50 * * * * . /home/mike/.Xdbus; /home/mike/chg_background.sh >| OUT_BACKGROUND 2>&1
```

Don't forget the "." after the last asterisk.

---

### Post by geirha on 2008-10-20
gconftool using dbus as backend certainly made things harder, but it's a nice workaround for it you made. Thank you for that, now there should be one less "gotcha" for me when I decide to upgrade to intrepid. :)

BTW: Instead of listing 00-50 for minutes, you can use */10 to have it run every ten minutes. Not all cron implementations accept that syntax, but cron in Ubuntu does.

---

### Post by Chilly_Willy on 2008-10-27
Thanks, this solved my problem too.

---

