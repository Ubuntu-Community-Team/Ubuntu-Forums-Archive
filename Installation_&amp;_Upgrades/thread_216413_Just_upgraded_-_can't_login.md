---
title: "Just upgraded - can't login"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by Zooropa on 2006-07-15
Hi folks,

Relative newbie.

I upgrades from Beezy Bager today to Dapper Drake, and now I can't login.

When I put in my username/password the screen changes as though I'm logging in, and then in I'm taken back to the login page.

I have my username and password correct, so it's NOT that.

Any ideas?

How easy would it be for me to re-install it from scratch without upsetting my XP dual boot with GRUB?
I can't fully switch over as I develop in .NET.


I have an ATI card set up with a VESA driver as I did with breezy badger.

---

### Post by tseliot on 2006-07-15
> **Zooropa said:**
> Hi folks,

Relative newbie.

I upgrades from Beezy Bager today to Dapper Drake, and now I can't login.

When I put in my username/password the screen changes as though I'm logging in, and then in I'm taken back to the login page.

I have my username and password correct, so it's NOT that.

Any ideas?

How easy would it be for me to re-install it from scratch without upsetting my XP dual boot with GRUB?
I can't fully switch over as I develop in .NET.
Try creating a new user.
boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
adduser the_new_username
```

NOTE: replace "the_new_username" with your new username

then:
```
passwd the_new_username
```

and type the password for the new user

(like before, replace "the_new_username" with your new username)


Restart your computer:
sudo reboot

Boot as usual and log in with the new username and password.

You will need to move your files from "/home/your_old_username" to "/home/your_new_username"

---

### Post by Zooropa on 2006-07-17
Hi

That worked, and I'm in!

Thanks

However, "zooropa" - the account which has login problems was the "sudo" user.

This new account "skidmerc" doesn't seem to have any priviliges.

For example:

skidmerc@cpc2-kirk1-5-0-cust112:~$ cd /usr/src
skidmerc@cpc2-kirk1-5-0-cust112:/usr/src$ mkdir alsa
mkdir: cannot create directory `alsa': Permission denied
skidmerc@cpc2-kirk1-5-0-cust112:/usr/src$ sudo mkdir alsa
skidmerc@cpc2-kirk1-5-0-cust112:/usr/src$ cd alsa
bash: cd: /alsa: No such file or directory


It didn't create the directory.
Am I missing something?

When I go to System > Administration there are only 6 options - the Users admin option isn't there.

I've tried sudo usermod -G admin skidmerc but that didn't work.

---

