---
title: "Problem with reinstallation of Ubuntu on Dell M5110"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by cikaRadule on 2013-04-26
First I wish to say hi to all of you folks out there :)

I've been using Ubuntu for quite some time and having a lot of fun with it.
I even had a success in "converting" few of the people I know to the Ubuntu side. :)
But, there is where the problem came up...

My girlfriend got herself nice (red :) ) Dell M5110 laptop. I was happy to see that it came with preinstalled Ubuntu distro.
But, at the time, she was more into Windows OS so I had to remove Ubuntu and install Win 7.

Now she finally came to her senses and asked me to set her Ubuntu on her laptop (because mine is so cool).
But when I tried to do so I ran into big problems.
At first it was hard to get Ubuntu to start installation. So I remembered that Win also had problems when I tried to install it from USB stick, so I've burned installation cd.
That way I managed to install Ubuntu 12.04 (version linked on official page for Dell M5110 - [http://www.ubuntu.com/certification/hardware/201105-8042/](http://www.ubuntu.com/certification/hardware/201105-8042/)).
Install also had problem starting, until I googled that nomodeset should be checked. After checking nomodeset install was completed without any problems.
And as soon as it was completed - Ubuntu was dead. It asked to reboot, to eject cd and when it starts booting - nothing, black screen.

Does anybody have any idea what can I try?

Cheers

---

### Post by cikaRadule on 2013-04-28
After many more try and fail, I've managed to google out a solution for this.
Main problem was - graphic card. So I tried suggestion made [here]("http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/") and it worked :)

---

