---
title: "Why does it still take 2 mins to connect to wireless?"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2010-04-02
I've been using Ubuntu since 8.04 but jumped ship when Windows 7 was released. I was also a beta tester for Karmic. So, after hearing all the great news about how good 10.04, I decided to download it, to try it out. Its very much improved and I really like what I see so far. I like the bold approach :D. Now, one problem that seems to have been around for awhile is that Ubuntu is very slow at connecting to hidden wireless networks on startup.

In windows 7 for example, as soon as im on the desktop, my connection is connected and im able to surf without waiting 2 minutes like I do in Ubuntu. Is it because 10.04 is still in BETA or theres something wrong with the notebook I am using? The card thats in my notebook (Sony Vaio NR series) is Wireless LAN : Intel® PRO/Wireless 3945ABG

---

### Post by conradin on 2010-04-02
I had a laptop with that particular wifi card, and i definately recall having issues. I know that intel had supported the card at one time but i think they halted. 
Try these sites. I know I got mine working after a little tooling with it.

[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Wireless+Networking&ProductLine=Intel%C2%AE+WiFi+Products&ProductProduct=Intel%C2%AE+PRO%2fWireless+3945ABG+Network+Connection](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Wireless+Networking&ProductLine=Intel%C2%AE+WiFi+Products&ProductProduct=Intel%C2%AE+PRO%2fWireless+3945ABG+Network+Connection)

---

### Post by tjeremiah on 2010-04-02
> **conradin said:**
> I had a laptop with that particular wifi card, and i definately recall having issues. I know that intel had supported the card at one time but i think they halted. 
Try these sites. I know I got mine working after a little tooling with it.

[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Wireless+Networking&ProductLine=Intel%C2%AE+WiFi+Products&ProductProduct=Intel%C2%AE+PRO%2fWireless+3945ABG+Network+Connection](http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Wireless+Networking&ProductLine=Intel%C2%AE+WiFi+Products&ProductProduct=Intel%C2%AE+PRO%2fWireless+3945ABG+Network+Connection)

ok ill try, thanks :D

---

### Post by kerry_s on 2010-04-02
you just need to edit it & check the box "available to all users" then it will have the info to connect at boot before the desktop.

---

### Post by tjeremiah on 2010-04-02
> **kerry_s said:**
> you just need to edit it & check the box "available to all users" then it will have the info to connect at boot before the desktop.

thanks, ill give that a shot and report back.

---

### Post by lisati on 2010-04-02
> **tjeremiah said:**
>  The card thats in my notebook (Sony Vaio NR series) is Wireless LAN : Intel® PRO/Wireless 3945ABG
/me makes mental note: that's the card lspci reports for my Toshiba laptop. (Haven't had a problem with 9.04. Then again, I hardly ever use wireless, and although I have a copy of the Beta1 live CD I haven't done a proper test drive of 10.04 yet.)

---

### Post by aysiu on 2010-04-02
Is it this bug?
[network manager slow to reconnect after suspend/resume](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405)

I'm experiencing it too.

---

### Post by tjeremiah on 2010-04-02
> **aysiu said:**
> Is it this bug?
[network manager slow to reconnect after suspend/resume](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274405)

I'm experiencing it too.
yes, that is how it was behaving, not only on suspend/resume but also on startup. BUT the suggestion above from  kerry_s works :D . I just rebooted and my connection was ready from the get-go which was my main concern.

---

### Post by aysiu on 2010-04-02
> **tjeremiah said:**
> BUT the suggestion above from  kerry_s works :D Even for resume (as opposed to a reboot)?

Well, I'll test it out later today.

Nevertheless, that's a workaround. It's still a bug.

---

### Post by tjeremiah on 2010-04-02
> **aysiu said:**
> Even for resume (as opposed to a reboot)?

Well, I'll test it out later today.

Nevertheless, that's a workaround. It's still a bug.

:( Ok, I just tested it again and after resume, my network goes completely dead. Can't connect to anything and have to reboot. Its a small issue for now though. I dont really suspend much.

---

### Post by kerry_s on 2010-04-02
> **tjeremiah said:**
> :( Ok, I just tested it again and after resume, my network goes completely dead. Can't connect to anything and have to reboot. Its a small issue for now though. I dont really suspend much.

sounds like you got 1 of those drivers you need to suspend.

do this in terminal: 
**sudo cp /usr/lib/pm-utils/defaults /etc/pm/config.d/defaults**

**gksudo gedit /etc/pm/config.d/defaults**

look for this line: 
[B]# If you need to unload any modules to suspend/resume, add them here.
# SUSPEND_MODULES=""
[/B]
uncomment it & put your wireless driver in there, you can look at "**lsmod**" to see what driver your using.
for example mine uses the b43 driver, so it would be like this:
**SUSPEND_MODULES="b43"**

---

