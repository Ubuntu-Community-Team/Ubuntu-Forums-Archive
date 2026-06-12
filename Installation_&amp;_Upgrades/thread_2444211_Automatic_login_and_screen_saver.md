---
title: "Automatic login and screen saver"
date: 2020-05-26
forum: Installation &amp; Upgrades
---

### Post by amikot2 on 2020-05-26
Is that correct and planned that Ubuntu installed with option "Automatic Login" is asking for password when returning from screen saver?
I would say this is mistake of developers. Its not increasing safety at all and is really annoying - for some people it may be easier and quicker to restart the system instead of entering the password.

---

### Post by GhX6GZMB on 2020-05-26
Yeah, it's annoying. It's not a Ubuntu issue, it comes from Lock Screen. You can turn it off.

---

### Post by amikot2 on 2020-05-26
I understand it comes with Lock Screen, but I believe that developers could turn it off automatically if user selected automatic login on installation screen. Its not only thing that's annoying - that's one of these small things to complain about when you moving from Windows.

---

### Post by DuckHook on 2020-05-26
While I have slightly modified my views on automatic logins (only for highly specific applications like Kodi where challenge/response can break actual functionality), those views largely remain as before: auto login should not even be offered in the first place.

The vast, vast proportion of people who resort to automatic login are doing nothing more than indulging their bad habits. In most cases they are dragging their dangerous Windows habits with them into Linux. There is no excuse for turning off challenge/response authentication. It is a fact of nature that we are creatures of habit. Good habits lead to clean computing hygiene, bad habits lead to dirty hygiene. Reinforcing/enabling bad habits is the primary reason that Windows is such a malware cesspool.

It is an unarguable fact that passwords increase safety and just as unarguable a fact that automatic logins destroy safety. But this is predicated on taking the challenge/response philosophy seriously. Those who don't like passwords are the same ones who use passwords like "password", then claim that passwords are a useless security measure because they got hacked. :roll:

If you want to destroy Linux password security, there are thousands of tutorials all over the Internet that show you how to do so. It is a testament to Linux's dedication to computing freedom that users are at liberty to do even the most self-destructive things. But just because you *can* is no affirmation that you *should*.

---

### Post by GhX6GZMB on 2020-05-27
> **amikot2 said:**
> I understand it comes with Lock Screen, but I believe that developers could turn it off automatically if user selected automatic login on installation screen. Its not only thing that's annoying - that's one of these small things to complain about when you moving from Windows.

Autologin and Lock Screen are two different things and are not really connected. Autologin is a system login thing, and if you want to use it's your choice (not a good one, but OK).

Lock Screen is a different issue. It can be turned off in Preferences > LXQt Settings > Session Settings if you like.

Imagine that you have your machine set to autologin. That's fine, because you have it in your possession when turning it on. But suppose you have to leave the machine unattended: in that case a Lock Screen would be a good option, no?

Just an example.

---

### Post by deadflowr on 2020-05-27
> Lock Screen is a different issue. It can be turned off in Preferences > LXQt Settings > Session Settings if you like.
Ubuntu doesn't have that setting.:(

But it does have a screen lock setting in Settings > Privacy.

---

### Post by GhX6GZMB on 2020-05-27
> **deadflowr said:**
> Ubuntu doesn't have that setting.:(

But it does have a screen lock setting in Settings > Privacy.

My bad :(

Dunno where I got the idea that this was a Lubuntu installation. Brain fart, I guess...

---

### Post by grahammechanical on 2020-05-28
> for some people it may be easier and quicker to restart the system instead of entering the password. 				

How can that be true? In my experience a system restart is not that quick as the OS has to shut all kinds of services down and then trigger the motherboard boot process. It includes the Grub bootloader and if dual booting a 10 second delay before loading the first OS in the list.

 A hard power off at the computer case is a bit quicker but it is a drastic way of doing things and it is thanks to Linux developers that it does not often mess up the OS. I have found that sometimes a proper system shut down and reboot is then needed to sort out the mess of a hard reboot. A much longer process than typing in an assorted combination of keyboard characters.

Regards.

---

