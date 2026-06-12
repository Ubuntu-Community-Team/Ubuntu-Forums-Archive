---
title: "upgrading from 21.04 to 21.10"
date: 2023-05-08
forum: Installation &amp; Upgrades
---

### Post by artynet on 2023-05-08
Hello folks,

I'm basically stuck to Kubuntu 21.04 since I can't run the distribution upgrade. The 21.10 repositories are now in the archived mirror section and a straight upgrade to the next release does not seem possible (the system suggest me to switch to 22.04 LTS). My last chance, I think, is to manually switch the repositories list itself with this ones:

```

deb http://old-releases.ubuntu.com/ubuntu impish main restricted universe multiversedeb-src
deb http://old-releases.ubuntu.com/ubuntu impish main restricted universe multiverse

deb http://old-releases.ubuntu.com/ubuntu impish-security main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu impish-security main restricted universe multiverse

deb http://old-releases.ubuntu.com/ubuntu impish-updates main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu impish-updates main restricted universe multiverse

deb http://old-releases.ubuntu.com/ubuntu impish-proposed main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu impish-proposed main restricted universe multiverse

deb http://old-releases.ubuntu.com/ubuntu impish-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu impish-backports main restricted universe multiverse

```

and then simply run:

```

# sudo apt update
# sudo apt dist-upgrade

```

to perform the whole upgrade. Does it sound right to you? Please let me know....thanks in advance.

       Kind Regards

---

### Post by yancek on 2023-05-08
It might work, not sure but I'm not sure why you would want to upgrade to 21.10 since it is also unsupported since last summer.  Simpler to back up your personal files and install 22.04.

---

### Post by tea for one on 2023-05-08
> **yancek said:**
>  Simpler to back up your personal files and install 22.04.
Perfect advice.
You'll be up and running in an hour or so.

---

### Post by artynet on 2023-05-08
Thank you for the quick reply guys...

My final goal is to run multiple distribution upgrades until reaching the latest kubuntu 23.04. The fact is that the upgrades are allowed only for adjacent releases (i.e. 21.04 -> 21.10) and not with an abrupt jump of two sequential ones (i.e. 21.04 -> 22.04). That might crash the whole system.

Hence the need to switch to the archived **impish** repositories and then proceed with the regular **22.04 LTS** upgrade

---

### Post by Impavidus on 2023-05-08
It may work, but better to jump to 22.04 directly. You can install 22.04 over 21.04 without formatting, which will note the currently installed packages and upgrade all to the versions for 22.04 (provided they're available for the new release).

---

### Post by kc1di on 2023-05-08
You would be much better off upgrading to 22.04 LTS.
[https://www.omgubuntu.co.uk/2022/04/how-to-upgrade-to-ubuntu-22-04-lts]("https://www.omgubuntu.co.uk/2022/04/how-to-upgrade-to-ubuntu-22-04-lts")

---

### Post by artynet on 2023-05-08
I have never done such upgrade, always one by one release....are you sure this is safe to run ? 

[https://askubuntu.com/questions/1410030/issue-upgrading-21-04-to-22-04-only-shows-21-10-upgrade-option](https://askubuntu.com/questions/1410030/issue-upgrading-21-04-to-22-04-only-shows-21-10-upgrade-option)

According to this thread only single release upgrade are permitted....

---

### Post by tea for one on 2023-05-08
> **artynet said:**
> I have never done such upgrade, always one by one release....are you sure this is safe to run ?
If you are referring to the omgubuntu article, it is not the solution for you.
You are using 21.04 (not 20.04 or 21.10)

---

### Post by artynet on 2023-05-08
No I am not.  The article is from AskUbuntu forums:

[https://askubuntu.com/questions/1410030/issue-upgrading-21-04-to-22-04-only-shows-21-10-upgrade-option](https://askubuntu.com/questions/1410030/issue-upgrading-21-04-to-22-04-only-shows-21-10-upgrade-option)

which firmly states that such abrupt upgrade is not possible. For this very reason, I want to manually :


[LIST]
[*]switch to the 21.10 archive repositories 
[*]apt get update && apt dist-upgrade 
[/LIST]

once booted in impish 21.10, I will be able perform the regular distro update to 22.04, 22.10 and so on.....that should be the proper way to do it.

---

### Post by oldos2er on 2023-05-08
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

But as was mentioned it would be much less time consuming to backup your data and clean install 22.04 (or other supported version).

---

### Post by Impavidus on 2023-05-08
An upgrade by reinstall is also an option. Install the new version over the old, without formatting, and it should keep your installed software (provided it's still available), configuration and documents. It's faster and more reliable than upgrading twice (21.04->21.10->22.04) or performing an unsupported upgrade (21.04->22.04).

---

### Post by MAFoElffen on 2023-05-08
> **oldos2er said:**
> [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

But as was mentioned it would be much less time consuming to backup your data and clean install 22.04 (or other supported version).
To demonstrate... Doing the math on what you are proposing, let's say conservatively that it takes 3 hours to do a release upgrade of a fully loaded install. You are talking about 21.04 to 21.10, 21.10 to 22.04, 22.04 to 22.10, and 22.10 to 23.04. 4 stages, where you have 4 potential risks at failure, that the risk factor multiplied with each stage iteration.

3 hours each at 4 stages... Potentially 12 hours or longer.

New, fresh install. Re-Install manually installed applications. Restored data = 20 minutes, to an hour.

Hmmm. Decisions. Decisions. Just joking about it being a conundrum, but you can see the logic in that right?

That is why so many people are recommending against it.

---

