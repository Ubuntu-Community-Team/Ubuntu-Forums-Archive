---
title: "Login loop after upgrade to 11.04"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by crazycoders on 2011-04-28
I just finished the upgrade of 10.10 to 11.04, restarted and now i can't login anymore, i'm stuck in an endless login loop.

1) Boot
2) Xorg starts
3) I see my user, login
4) Screen goes black like it's loading
5) Loop back to login

It's not a password issue, i can login in command line
It's not a profile issue cause i tried creating a new user from the command line and it still loops.
I looks briefly at the /var/log/... but i couldn't find anything relevant, please respond ASAP this is my work PC.

I thought it would be simple since it's a very simple a relatively new machine (2months ago)

Math

---

### Post by crazycoders on 2011-04-28
More info, seems that if i use the button at the bottom of the screen and choose another login mode (Ubuntu Classic No Effects) it works. This might be an effect's issue, i turned it off when installing 10.10 because my video cars (crappy ATI) didn't support it. I'm trying another mode now to see if theres the unity version without effects, didn't see it at first.

Math

---

### Post by crazycoders on 2011-04-28
Tried to uninstall compiz, still no avail, i can't seem to use the standard ubuntu desktop or ubuntu classic desktop with 11.04...

I'll wait for anwsers from other people now, i got work to do and at least i can work on my old desktop.

---

### Post by slooksterpsv on 2011-04-28
I had this issue before and I had to dump some of the cache files from my user account. So, you could try (and we'll move it just in case it doesn't work) this:
Press CTRL+ALT+F1
Type in your username (press enter afterwards)
Type in password (won't show on the screen) (press enter afterwards)

Now type the following:
```

mv ~/.config ~/.config_old
mv ~/.local ~/.local_old
mv ~/.gconf ~/.gconf_old
mv ~/.gconfd ~/.gconfd_old

```

Then restart. Some of your application settings won't have what you previously had, but I've had to do this with a looping login due to corrupt config. If that doesn't work, just reverse .config with .config_old and .config_old to .config above for each.

---

### Post by cwk on 2011-05-03
I'm having the same trouble. Login loops regardless of the session I choose. 

I tried the recommendation in this thread, but no luck. Any other suggestions would be appreciated.

---

### Post by slooksterpsv on 2011-05-04
> **cwk said:**
> I'm having the same trouble. Login loops regardless of the session I choose. 

I tried the recommendation in this thread, but no luck. Any other suggestions would be appreciated.

Hmmm... again I think I said this above, but I know when my app properties were corrupt that worked. Try this:

Press CTRL+ALT+F1
Type in your username and password (password won't show when it asks for it)
Type in: sudo killall gdm-binary
Press CTRL+ALT+F1
Type in: sudo gdm
Try to login
If the same thing happens again press CTRL+ALT+F1 and see what the lines say.

Or try to create a new user:
Do the following above up until after the 2nd CTRL+ALT+F1
Type in: sudo adduser test
Fill out the password, first name, last name, etc. then
Type in: sudo gdm
Try to login with the new test user using the password you created above.

If that doesn't work, try:
sudo dpkg-reconfigure gnome-session
sudo dpkg-reconfigure gdm

Reboot and try to login. Ummm... I dunno what else to try. Or if you can try to do a dist-upgrade:

sudo apt-get update && sudo apt-get dist-upgrade

The only other thing I can think of is to install another desktop environment like LXDE:

sudo apt-get install lxde

Then login using LXDE instead of Ubuntu or Ubuntu Classic

I'm out of ideas past that.

---

### Post by ulukay on 2011-05-06
same here :(

[http://ubuntuforums.org/showthread.php?t=1750548](http://ubuntuforums.org/showthread.php?t=1750548)

using kdm instead of gdm works
but you'll lose functionality :(

edit: found the problem :)

---

