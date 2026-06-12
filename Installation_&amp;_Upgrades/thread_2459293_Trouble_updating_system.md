---
title: "Trouble updating system"
date: 2021-03-15
forum: Installation &amp; Upgrades
---

### Post by don-alvareto on 2021-03-15
Hi, I'm new to Ubuntu and recently tried to update the system through this command:

```
sudo apt update && sudo apt upgrade -y
```

But it didn't work. It returned this error message:

[ATTACH=CONFIG]288137[/ATTACH]

I also tried updating the system through the Software Updater but it constantly tells me to check my internet connection every time I try to download and install the updates. I'm currently on this Ubuntu version:

[ATTACH=CONFIG]288138[/ATTACH]

What can I do?

---

### Post by CatKiller on 2021-03-15
> **don-alvareto said:**
> What can I do?
Disable the unused cd-rom and unsigned opera repositories and try again.

---

### Post by Impavidus on 2021-03-16
1: That command will download and install all upgrades without further quations. Some people do so, I prefer to see what it will do before proceeding. Not really a problem though.

2: Ubuntu 16.04 is quite old and only has one month of support left. If you're new to Ubuntu, why start with such an old release?

3: The cdrom repository can be useful on offline systems to install some additional software you may need to get online. It can be disabled in your software sources.

4: The no public key error can be fixed by downloading and installing the missing keys. See [https://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey](https://askubuntu.com/questions/13065/how-do-i-fix-the-gpg-error-no-pubkey)

5: The output you get in a terminal is just text. You can paste it as text on the forum, in code tags, like you did with the command. That makes it easier for us to incorporate parts of it in a reply.

---

### Post by ActionParsnip on 2021-03-16
Xenial is end of life REALLY soon. You may want to wipe it off and do a clean install of Focal (Ubuntu 20.04). Alternatively, you could update to Bionic (Ubuntu 18.04) as LTS to LTS upgrades are supported.
Why such an ancient release?

---

### Post by ActionParsnip on 2021-03-16
To fix your key issue, run
```

wget -qO - https://deb.opera.com/archive.key | sudo apt-key add -

```

Source:
[https://deb.opera.com/manual.html](https://deb.opera.com/manual.html)

---

