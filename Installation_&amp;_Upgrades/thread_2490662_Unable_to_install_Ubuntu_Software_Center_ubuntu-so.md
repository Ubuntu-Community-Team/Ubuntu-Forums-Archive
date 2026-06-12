---
title: "Unable to install Ubuntu Software Center ubuntu-software"
date: 2023-09-11
forum: Installation &amp; Upgrades
---

### Post by rdnublx on 2023-09-11
I assume that the Software Center should be a part of Ubuntu installation. Is that a correct assumption? And is the Software Center a preferred or recommended tool for software installation and maintenance on Ubuntu?

Anyway, I tried to install it, first updating the package lists, as follows:
```
sudo apt update -y
sudo apt install ubuntu-software -y
```
Update of the packages list completed fine. However, the installation command did not, generating an error:
```
E: Unable to locate package ubuntu-software
```
I would appreciate guidance on this topic and any additional commentary possibly related to the issue. Thank you

---

### Post by MAFoElffen on 2023-09-11
Try this
```

## Install the Software Center for Gnome
sudo apt install gnome-software

```

---

### Post by rdnublx on 2023-09-11
Thank you, let me try. I came across this recommendation on some website, after I already posted here, but did not want to take a chance. I don't have a lot of experience with this package management and dependencies, was not sure.
Anyway, give me a few moments to try and post back here. I do appreciate your help

---

### Post by rdnublx on 2023-09-11
It actually worked fine, thank you again. There is a new app installed called Software, rather than Software Center. And the icon looks different from what I expected. It's a white suitcase with three geometric shapes, rather than the expected orange suitcase with a letter A in the middle. However, upon opening, the app GUI looks similar to what I expected.
I assume I should be able to install Firefox with it, without worrying how to manage it using snap or apt. It's just puzzling why would software center and something like Firefox be missing from my distribution. 
Anyway, thank you again. Do I need to mark this as a resolution, or it's not how it works on this platform?

---

### Post by MAFoElffen on 2023-09-11
The old "Ubuntu Software Center" was replaced a while ago: [https://www.omgubuntu.co.uk/2015/11/the-ubuntu-software-centre-is-being-replace-in-16-04-lts](https://www.omgubuntu.co.uk/2015/11/the-ubuntu-software-centre-is-being-replace-in-16-04-lts)

Remember to use the Thread Tools link in the upper right to mark this as Solved so that others may find your solution. Good luck.

---

### Post by oldfred on 2023-09-12
Any default install of Firefox from Ubuntu will use the snap.
Even snaptic which I prefer over Software center, now installs the snap.

You also have to reset priorities as shown or it will reinstall the Firefox snap.
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)

---

### Post by rdnublx on 2023-09-12
Thank you again, of course will mark it as Solved, I now see the Thread Tools menu at the top.
I read the post you provided. Interesting that it was quite a while ago, because I followed a fairly recent guidance as of July 2023, [https://adamtheautomator.com/ubuntu-software-center/](https://adamtheautomator.com/ubuntu-software-center/) , which looked credible and well written / informed. Maybe it's just the reference "ubuntu-software" that was removed recently, while the software center was replaced at the time of post you provided here. Anyway, it's irrelevant, I am good now, and thank you.

---

### Post by rdnublx on 2023-09-12
Thank you for your reply and the information, appreciate it. 
Yes, I already installed Firefox via the Software app. It certainly looks like it uses Snap framework under the cover, based on the indicator in the upper right corner. I realize that many people don't like Snap for various reasons. I am fine with it, until and if I encounter issues. Based on my reading, it appears to me that if one wants to avoid Snap, using Ubuntu is not the best idea. I will just have to accumulate my own experience, at this point just continuing with default systems, so far working fairly smoothly. Your information is very helpful, particularly the Kubuntu Firefox post. 
Thank you.

---

