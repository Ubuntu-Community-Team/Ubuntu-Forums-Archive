---
title: "Upgrade without downloading your packages again."
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by smss on 2012-11-29
My Ubuntu version is 11.04 and I wanna upgrade it to 12.04.
But for this purpose I have to re download my installed packages.
How can I reach to this purpose without downloading them again?( I have a ISO Ubuntu 12.04 whom I can burn it on a disk. )
I search about it and I found a way which I'm not sure about it.
The mentioned way is :
```

dpkg --get-selection > package_list
dpkg --set-selection < package_list

```What is your opinion about it?
are you believe that it can reach us to that point?

---

### Post by Sergius14 on 2012-11-29
Why you have to download them again?

The upgrade process is for just migrate your apps and home user.


I think that your aproach may fail misserably....

---

### Post by smss on 2012-11-29
> **Sergius14 said:**
> Why you have to download them again?

The upgrade process is for just migrate your apps and home user.


I think that your aproach may fail misserably....
Are you saying the Upgrade process do not change and remove the installed packages by user?

---

### Post by ibjsb4 on 2012-11-29
> **smss said:**
> Are you saying the Upgrade process do not change and remove the installed packages by user?

Yes, in theory your offical ubuntu packages will also be upgraded in the process.  The exception being any packages that are not offered in 11.10/12.04 and PPA's will not be upgraded.  Your 11.04 release has reached EOL so you can try upgrade and see how it goes.

Your upgrading to Unity/Gnome3, I say you can expect some breakage.

---

### Post by Paddy Landau on 2012-11-29
I upgraded a computer from 11.04 to 12.04 and it worked without any problems. (I don't remember if I had to upgrade via 11.10.)

However, you may have to add back any PPAs that you have manually added.

Just be sure to **make full backups** before you start; any upgrade always carries a risk.

---

### Post by smss on 2012-12-01
How can get a backup from GPG secret keys?

---

### Post by Paddy Landau on 2012-12-02
> **smss said:**
> How can get a backup from GPG secret keys?
I would post this request as a new thread in the [Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338").

---

### Post by oldfred on 2012-12-02
Thanks, I created my launchpad account when I was running Maverick and my keys are still in that /home. I need to copy those.

Back up gpg key
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

---

