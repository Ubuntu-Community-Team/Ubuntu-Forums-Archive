---
title: "Upgraded to DEVELOPMENT BRANCH and freaking out"
date: 2017-03-14
forum: Installation &amp; Upgrades
---

### Post by logandark2 on 2017-03-14
My server upgraded itself to Zesty Zapus today (notice the bold):

```
Welcome to Ubuntu Zesty Zapus (development branch) (GNU/Linux 4.8.0-41-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

3 packages can be updated.
0 updates are security updates.


No mail.
Last login: Tue Mar 14 09:21:33 2017 from 192.168.1.4
logandark@LD-Server:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Zesty Zapus (development branch)
Release:	17.04
Codename:	zesty
logandark@LD-Server:~$
```

I don't want this. I need to know how to downgrade it back to 16.10. I had a stable version going and something ruined it.

I don't care what I have to do, I need to downgrade it. I have no backups or anything really. Please tell me how. I don't care how dangerous it is. I need my stable 16.10 back.

---

### Post by ian-weisser on 2017-03-14
Backup your data right now.
Then do a test restore from your backup so you know it really works.
Then fresh-install the version of Ubuntu you wish to use.
Then restore your data from the (validated) backup.

Let's be clear: Your system didn't become self-aware and decide to upgrade itself for fun. Release-upgrade settings are controlled by the human.

---

### Post by logandark2 on 2017-03-14
[FONT=courier new]apt-get upgrade[/FONT] decided I'm on the development branch now. **I never enabled that**. But that's besides the point.

I'm not going through the install process again. It's too much work at the physical server. I need to downgrade it through SSH.

---

### Post by QIII on 2017-03-14
Neither upgrade nor dist-upgrade will cause an upgrade to a newer release.  They upgrade software packages in the current release.

There is no "downgrade" path.  There is only backup and reinstall, as suggested.

---

### Post by T.J. on 2017-03-14
Qill is quite correct.  The DEB packaging system is not designed for downgrading, so the best method is to reinstall.  It is possible to force the issue using a technique known as "apt pinning", but it is highly unadvisable if you are not a developer. It can leave the system in an unusable state.

If I might say so, if you require stable behavior, you should stick with LTS releases.

---

### Post by SeijiSensei on 2017-03-14
> **T.J. said:**
> If I might say so, if you require stable behavior, you should stick with LTS releases.
^This.  If you do reinstall, use 16.04LTS.  Any production server should always use LTS versions.  I have servers still running CentOS 6.x and don't intend to upgrade them to version seven any time soon.

---

### Post by logandark2 on 2017-03-14
Guess what? I didn't tell it to upgrade to 17.04. I was happily on 16.10 this morning and then in the middle of the day I logged in and saw 17.04.

If I had a choice I would have stuck with 16.10.

---

### Post by QIII on 2017-03-14
A release upgrade requires human agency -- such things as modifying sources.list or issuing the command do-release-upgrade.  There are also settings that upgrade the release when a new one comes out -- even updating to a development release when it comes out.  Again, those settings are done at the hand of a human.

Neither your OS nor your machine just up and decides to do that.

Is your server secure?  Are others allowed physical access?  Do others have remote access?  Is your server exposed to the web?

---

### Post by ian-weisser on 2017-03-14
> **logandark2 said:**
> Guess what? I didn't tell it to upgrade to 17.04. I was happily on 16.10 this morning and then in the middle of the day I logged in and saw 17.04.

If I had a choice I would have stuck with 16.10.

You know, it's worth a moment to verify that you're really on 17.04 and it's not just a (very) unfortunate string substitution mistake.
The logfiles in /var/log/dist-upgrade will confirm that your system upgraded quietly this morning. It will also tell you exactly what time it was triggered - a clue to figuring out why.

---

