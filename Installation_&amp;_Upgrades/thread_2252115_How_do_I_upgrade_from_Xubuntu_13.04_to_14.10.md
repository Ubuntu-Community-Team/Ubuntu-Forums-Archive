---
title: "How do I upgrade from Xubuntu 13.04 to 14.10?"
date: 2014-11-09
forum: Installation &amp; Upgrades
---

### Post by postt on 2014-11-09
Hi,

I'm running Xubuntu 13.04. How do I upgrade it to 14.10?

Thanks.

---

### Post by plucky on 2014-11-09
> **postt said:**
> Hi,

I'm running Xubuntu 13.04. How do I upgrade it to 14.10?

Thanks.

See [EOL Upgrades](https://help.ubuntu.com/community/EOLUpgrades)

As 13.04 and 13.10 are both past EOL, probably better to clean Install Xubuntu 14.04.1 as it is an LongTerm Support (LTS) release.

Good Luck

---

### Post by postt on 2014-11-09
But why not 14.10? What's wrong with it?

Also when you said "install" did you mean overwriting my current system? That means I'd lose all the software I've installed? That's really not what I want. I just want to upgrade my system.

---

### Post by kc1di on 2014-11-09
At this point a clean install is the best way.  Back up what you want to save on external media first!

Nothing is wrong with 14.10 , but you may want to consider it only has 8 months of support left , 14.04 is Long term release and will be supported until 2019 
where 14.10 will only be supported until 2016.  So you could be in the same boat is a short time. if you are worried about your data being lost when you will need to upgrade again, It's better to go with the Long Term Support versions.  if you must have the latest and greatest in software and are not so concerned about stability of information then 14.10 is right for you .

14.10 does not have that much new in it for me to warrant changing from 14.04. 

Which ever you choose , back up that data and do a fresh install.
Good Luck :)

---

### Post by postt on 2014-11-09
I see. About backing up data - for things like documents and video files that's easy, but what about the software I've installed and the desktop environment I've configured (things like xfce widgets)? Is there any way to save those? Or are they all going to be lost and I'll just have to reinstall and reconfig everything? Thanks.

---

### Post by Impavidus on 2014-11-09
You can create a list of currently installed packages with```
dpkg --get-selections > package.txt
```storing the list in the file package.txt. Keep a backup of the file. On the new system you can run```
sudo dpkg --set-selections < package.txt
sudo apt-get dselect-upgrade
```to reinstall all packages. However, this is not very clean, as it will also reinstall things like dependencies that are no longer needed and it won't work if packages have changed name. Last time I went through the list and reinstalled only the packages of which I knew I needed them, dragging the dependencies in automatically.

If you keep all config files from your home directory and reinstall all xfce goodies and other software, all your original settings/configurations should still be there. One difficulty is that you get new versions of everything, and the old config files may no longer work.

---

### Post by vasa1 on 2014-11-09
> **Impavidus said:**
> ...
If you keep all config files from your home directory ... **old config files may no longer work**.
+1 ^^^. Not mentioned often enough. People go on about having a separate /home but don't talk much about the possibly outdated config files in there.

OP, no, you cannot upgrade from 13.04 to 14.10. Upgrades work only from one version to the immediate next one including from one LTS to the next. In this case, 13.04 was succeeded by 13.10 and 14.04. Also, as has been ponted out, you can't upgrade unsupported versions. So just bite the bullet and clean install 14.04 LTS (if you're averse to frequent upgrades) or 14.10 if you like to chance things a bit.

---

### Post by kc1di on 2014-11-09
as far as the xfce widgets go most of them will become outdated with the newer xfce4 install anyway and will have to be re-installed.

---

### Post by ian-weisser on 2014-11-09
> **postt said:**
> Also when you said "install" did you mean overwriting my current system? That means I'd lose all the software I've installed? That's really not what I want. I just want to upgrade my system.

Yes, he meant overwriting your current system.
Yes, he meant you will need to reinstall everything. Which, in Ubuntu, is extraordinarily *easy* and *fast*.

When you refer to 'system' and 'software' as separate entities, each of which can be updated separately...that's not Ubuntu.
Ubuntu and Debian are designed to upgrade both system and applications at the same time. They are tightly integrated.

Do be aware that your 13.04 system has not been receiving security updates for almost a year. If that system is exposed to the big, dirty internet, it has been vulnerable to several known, published exploits for a long time. Another good reason to reinstall from scratch.

---

### Post by grahammechanical on 2014-11-09
Did you check out the link to End Of Life upgrades in the second post? It is your choice.

I advise deactivating any proprietary video driver being used and revert to the default open source video driver; disable any PPAs; revert the desktop user interface to the default status, default themes and icon sets and that stuff; back up your important data. And be prepared to re-install any applications that were installed but not available from the software centre. Default applications usually get upgraded but non-default appllications may not get upgraded and may not work afterwards.

My advice would also be to stop at 14.04 or be prepared to upgrade every 6 months. It is your choice.

Regards.

---

