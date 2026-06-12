---
title: "Unable to Locate"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by deepeshkris on 2011-05-19
Hello 

I am trying to install Photorec / testdisk

I am entering this in terminal 
sudo apt-get install testdisk

sudo apt-get install photorec

For all these i am getting a message, "E: Unable to locate package testdisk" and similar message for Photorec.

I tried this even for Foremost but i am getting same message.

Any clue how do i get to open and work on these packages?

Thanks for your reply.

I am using ubuntu 10:10

DK

---

### Post by Toz on 2011-05-19
Have you run:```
sudo apt-get update
``` yet?

What is the result of the following commands?```
sudo apt-cache search testdisk
``````
sudo apt-cache policy testdisk
```

Testdisk & foremost are part of the universe repository - make sure it is enabled.

---

### Post by deepeshkris on 2011-05-19
> **Toz said:**
> Have you run:```
sudo apt-get update
``` yet?

What is the result of the following commands?```
sudo apt-cache search testdisk
``````
sudo apt-cache policy testdisk
```

Testdisk & foremost are part of the universe repository - make sure it is enabled.

Thanks for your reply, I just ran the update 

Then i tried to locate package testdisk
~ search testdisk gave no reply

I tried to sudo apt-cache policy testdisk it cou
"Results' Unable to locate package testdisk

How do i enable universe repository or check its enabled?
Please help me!

---

### Post by Toz on 2011-05-19
Post back the contents of your /etc/apt/sources.list file. Lets see if the universe repository is enabled. 

You can also check this by opening "Ubuntu Software Sources", selecting "Software sources" from the Edit menu, and making sure that "Community-maintained Open Source software (universe)" is slected.

---

### Post by Rubi1200 on 2011-05-19
If you are on a LiveCD/USB you need to enable the universe repository as mentioned by Toz.

Then, click on Reload and afterwards close the the application and open a terminal to run apt-get update again and then try and install the packages you need.

---

