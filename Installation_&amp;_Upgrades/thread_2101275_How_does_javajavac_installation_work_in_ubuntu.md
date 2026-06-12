---
title: "How does java/javac installation work in ubuntu?"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by kevincmaker on 2013-01-04
Recently I installed jdk 1.7 in ubuntu. These are the steps that I used to install it.

1. Extracted the folder named 'jdk1.7.0' and copied it to '/usr/lib/jvm'.

2. Installed javac using the following command
   sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.7.0/bin/javac 4

3. Installed java using the following command
   sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.7.0/bin/java 4

I use Ubuntu 12.10

But, I really don't understand why I did all these things and how they work but they did. Can anyone explain how they work in Ubuntu?

Thanks in advance!

Regards,
Kevin.

---

### Post by Pjotr123 on 2013-01-04
This is a more detailed how-to for installing Java manually:
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

With explanations of each command. :)

---

