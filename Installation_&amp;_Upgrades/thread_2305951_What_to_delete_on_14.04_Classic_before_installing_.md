---
title: "What to delete on 14.04 Classic before installing Mate?"
date: 2015-12-10
forum: Installation &amp; Upgrades
---

### Post by Erika_Romero on 2015-12-10
Hi,
I'm about to install Mate on my new desktop that already runs the Flashback session on Ubuntu 14.04. 
I have made a lot of changes in order to get the appearence I want. As I'm not happy with the result I found Mate very attractive and before I install it I need to be shure I do it the right way. 
(Sorry about my pour English)

---

### Post by furtom on 2015-12-10
You don't really have to delete anything. You are just adding another DE. There may be a few redundencies, this is true, but this is not really a big issue. If later, you are trully irritated at having two text editors or file managers, etc., you can just choose one to remove.

Since you are running 14.04, you'll need a ppa. Try [Installing MATE in Ubuntu 14.04 LTS]("http://www.omgubuntu.co.uk/2014/08/install-mate-desktop-ubuntu-14-04-lts"):

```
sudo apt-add-repository ppa:ubuntu-mate-dev/ppa
sudo apt-add-repository ppa:ubuntu-mate-dev/trusty-mate
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install --no-install-recommends ubuntu-mate-core ubuntu-mate-desktop
```

and see if you are not satisfied with the result.

I did something similar and I love it.

---

### Post by Dennis N on 2015-12-10
Hi Erika, is it your intention to install the MATE desktop to your existing Ubuntu 14.04, or to remove your Ubuntu 14.04 and install the Ubuntu MATE 15.10 distro to replace it? (download .iso from here: [https://ubuntu-mate.org/](https://ubuntu-mate.org/) and click on "Download" at the top.)

---

### Post by Erika_Romero on 2015-12-13
> **furtom said:**
> 

Thanks furtum and Dennis N for replies!

I didn't need more than one Ubuntu but I thought I had to.... Now I know Mate was complete and enough! Installed and beautifully reminding me of 10.04 Intrepid, the perfectly structured desktop!

---

### Post by furtom on 2015-12-14
Glad it worked out. I'm just curious, did you reinstall or just install the desktop?

---

### Post by Bucky Ball on 2015-12-14
Good news. Please mark as solved to help others if you are satisfied (first link in my signature). This won't close the thread to further discussion. Thanks and enjoy. :)

---

### Post by Erika_Romero on 2015-12-16
> **furtom said:**
> Glad it worked out. I'm just curious, did you reinstall or just install the desktop?

Hi,
I made a clean install after backing up all my files. Easy peasy!

---

