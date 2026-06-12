---
title: "Retarded issue: Can't upgrate to 11.04 from 10.10"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by 1dbzfanjake on 2011-04-17
Hey, this should be a reaally easy problem to fix, but I have spent 20 minutes looking and can't find the solution. I just installed 10.10 and want 11.04 now. Don't ask me why I didn't just install Natty Narwhal, but I didn't. Now, when I run the update manager, it does not mention the update to 11.04. So I run check, nothing. I open the settings, check every option I can because what the heck, and nothing. Now I can probably go and manually install the update, but I am quite lazy and also want to learn what the hell is wrong with my update manager. Any hints or suggestions? Thanks for even looking at this post
-Jake

---

### Post by garvinrick4 on 2011-04-17
Open a terminal and copy and paste one at a time:
```
sudo apt-get install aptitude
``````
sudo aptitude update && sudo aptitude upgrade
``````
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 

```##You have installed aptitude, upgrade your 10.10, changed sources list (repositories to natty)
and did a dist-upgrade.
##Instructions manual for all ubuntu versions for dist-upgrade and post install is in my signature says Main Page -

---

### Post by kostkon on 2011-04-17
11.04 is still beta, that's why you don't the option to upgrade in the update manager.

To upgrade, just do the following:
> To upgrade from Ubuntu 10.10 on a desktop system, press Alt+F2, type in "update-manager -d" (without the quotes), and press Enter. Update Manager will open up and display the message, "New distribution release '11.04' is available." Click Upgrade and follow the on-screen instructions.
as taken from the [beta release notes page]("http://www.ubuntu.com/testing/natty/beta")

---

### Post by TBABill on 2011-04-17
> **1dbzfanjake said:**
> Hey, this should be a reaally easy problem to fix, but I have spent 20 minutes looking and can't find the solution. I just installed 10.10 and want 11.04 now. Don't ask me why I didn't just install Natty Narwhal, but I didn't. Now, when I run the update manager, it does not mention the update to 11.04. So I run check, nothing. I open the settings, check every option I can because what the heck, and nothing. Now I can probably go and manually install the update, but I am quite lazy and also want to learn what the hell is wrong with my update manager. Any hints or suggestions? Thanks for even looking at this post
-Jake Update manager is simply not made to do what you want to do. Your options are never, normal releases or LTS releases only. 11.04 is beta, so it is not yet a release. Once released (end of the month) you'll be able to do it right from update manager if you mark it to handle normal releases.

---

### Post by sammiev on 2011-04-17
When I upgraded from 10.10 to 11.04 I had a lot of problems and crashes. Then did a fresh install with 11.04 and things were a lot better. GL :)

---

