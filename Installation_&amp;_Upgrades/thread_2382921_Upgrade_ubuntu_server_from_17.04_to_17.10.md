---
title: "Upgrade ubuntu server from 17.04 to 17.10"
date: 2018-01-18
forum: Installation &amp; Upgrades
---

### Post by mons-web on 2018-01-18
Hello,

I am using Ubuntu server 17.04
Today I just wanted to install some packages via apt-get, and I discovered it is not possible anymore since "[The 17.04 repositories have been closed and withdrawn.]("https://ubuntuforums.org/showthread.php?t=2382832")"

So, I looked on the web to find a way to upgrade, and it seems like I need a package called "update-manager-core", that I don't have yet.
But since the repos have been closed.. I just can't get the package...!

Do you guys know how I could proceed to make the upgrade ?
Can I download update-manager-core from somewhere else, if yes, how ?

Thanks

---

### Post by mons-web on 2018-01-18
PS: I don't know if it's a good idea, but actually if I could downgrade to 16.04 it wouldn't be bad either. Is it a good idea? easy to do?

---

### Post by SeijiSensei on 2018-01-18
Downgrading inplace is not really an option. Installing from scratch is the best answer.

More generally I would only use LTS versions on servers. Stability is much more important than the most recent releases for most server programs. I'd start testing the 18.04 beta on another machine or in a virtual machine. I'm running a desktop version of Kubuntu 18.04 at the moment and I've encountered only one little problem that is an issue for KDE itself, not the Kubuntu distribution.

---

### Post by mons-web on 2018-01-19
Hi @SeijiSensei 	

Thanks for your answer

Well honestly I'm kind of noob, and I didn't know at all there was long time/short time support versions, so when I rent my dedicated server I just installed the latest version, thinking it was a good idea to be up to date..
But I just use my server to run some websites, and now I'm kind of stuck. I'm a bit lazy to make a full install again, I will need to reinstall every package and I have a lot of website to migrate + I just don't have much time to do it since I have 1 million other things to do for my work :/

I will ask my question in another way:
What is the easiest and fastest way to get my server functional ? How can I migrate to 17.10 (since this solution sounds less long than downgrading) ?

Would really appreciate any help on this!

Thanks

---

### Post by mikewhatever on 2018-01-19
You can install packages on an unsupported release: [https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release](https://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release). Then try to upgrade, and if lucky, you'll get to 17.10, which is also a 9 months release. 
It's also a good idea to ask the service provider for recommendations. They might not support upgrades, or impose conditions, etc.

---

### Post by mons-web on 2018-01-19
Thank you very much @mikewhatever! It worked like a charm, I'm now able to upgrade. I will make some backups first ;) Now I'm relax for the next 9 months, and when I will have time I will install a LTS version

---

