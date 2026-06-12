---
title: "Ubuntu 12.04 LTS post installation, stable system, x64 skype"
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by Artpen on 2012-11-11
Hi guys,

I installed Ubuntu 12.04 a couple of weeks ago onto Dell Inspiron 17SE.
And I would like to keep my system stable until next LTS. 
I also have more specific questions:

1. I installed bumblebee and x-swat drivers, Do I need to remove their ppa ? How or why do I need to keep them?

2. Which ppa do I need to keep in order to get only stable canonicals updates?

3. I am using SSD, do i need to make defragmentation? How?

4. Very general question, what do i need to do to keep my system stable until next LTS?

Post installation problems:

5. I made /data partition while installing Ubuntu, inside /data I found "lost+found" folder. Why do I need it, and how get permissions to write in /data?

7. I will ask about x64 Skype installation later

8. I will ask about Flash installation later

Thanks for helping

---

### Post by Artpen on 2012-11-12
Here are some answers I found.

Q&A:
1. Yes, It is better to remove extra ppa

5. It is possible to remove lost+found folder. To change permission type:
    sudo -R username:username /data

8. Installed flash by typing:
    sudo apt-get install adobe-flashplugin

---

