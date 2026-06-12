---
title: "Annoying Unlock Login Keyring popup"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2012-12-15
Running 64 bit 12.04 and it runs great.

However, keep getting this 'Unlock Login Keyring' pop-up.
It asks to: Enter Password To Unlock your Login Keyring, when certain apps are opened. On first install I entered something to keep this pop-up from occurring but it started up again. 

Forgot what I did to stop them and can't seem to find it.
What do you have to do to stop these 'Unlock Login Keyring' pop-ups?

---

### Post by cybrsaylr on 2012-12-18
Any help here?

Discovered by going into 'Passwords and Keys' and unlocking the passwords login this popup stops but when you shutdown then restart your PC it's locked again and have to unlock it again every time. Is there a way to set it so it stays unlocked?

---

### Post by orb9220 on 2012-12-18
Yep had the same issue.

As wouldn't let me just hit enter keep requesting password.
Found two files in /home .local/share/keyrings. default and Default.keyring.

Deleted those two files and started gnome-gmail-notifier again.
This time a different dialog from keyring dialog. 

This had two line passwords prompt for master password?
Just Hitting Enter without entering anything worked with this prompt and gave me the unsecured warning and continued anyway. 

Which is different from the sea gnome keyring app single password prompt. 
Which just continues and continues asking for password with no way to cancel it.

And now now more bugging even on reboot.

---

### Post by cybrsaylr on 2012-12-18
Yeah, don't know what caused this to happen. All of a sudden,  Login Keyring popup keeps popping up. I can disable it by going into 'Passwords and Keys' and unlocking the passwords login but it doesn't keep this setting. Every time the PC is restarted this unlocking procedure has to be done again.

It's a real pain.

---

### Post by orb9220 on 2012-12-18
Nope to make it work you have to go into that location /home .local/share/keyrings 
and delete those 2 files in there and then start again.

Wouldn't give me the fresh one time original 2 password dialog until I did that. Then at the two password dialog just hit enter key nothing else. It will inform you of unsecured and just click Ok and then you won't be bugged anymore.

Not the most elegant solution. But until somebody chimes in with a better way. As I don't need my gnome-gmail-notifier running on startup to require me to log in keyring every damn time it runs on startup.

---

### Post by cybrsaylr on 2012-12-19
Tried following your, /home .local/share/keyrings.

I get to /home .local/share, then there is no /keyrings to go into to see those 2 files to delete.

---

### Post by orb9220 on 2012-12-19
[Check here]("http://askubuntu.com/questions/96798/where-does-seahorse-gnome-keyring-store-its-keyrings") and gives 2 different locations to check.

As using Mint 14 Cinnamon. Which is based on Ubuntu 12.10 so looks like their in different locations.
.

---

### Post by cybrsaylr on 2012-12-19
Yep that did the trick.
Those 2 files were in a different location,  ~/.gnome2/keyrings/ in Precise. Found and deleted them and it appears that pop-up has stopped.

Thanks  orb9220.

---

