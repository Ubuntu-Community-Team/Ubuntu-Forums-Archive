---
title: "Problems with Java Runtime Version 6 Update 25"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Crabaroni on 2011-04-29
I downloaded Java into my home folder instead of downloading it in my usr folder because it wouldn't let me(even when I was root user). It is present in my home folder with its own directory, but I am unsure how to use it. I downloaded Java to try to play Minecraft, but when I open then .jar file with the directory nothing happens. The actual directory contains the following folders:bin,javaws,lib,man,plugin,copyright,license,a read me file, thirdpartylicensereadme, and a welcome.html file. I don't like running Minecraft with OpenJDK because it lags tremendously and it won't close, and I heard the "real Java" runs it much better.Did I download it incorrectly, if so can you tell me how? I am really new to Linux so extra detail is appreciated.

---

### Post by PatrickD-52761 on 2011-04-29
Open a terminal and paste the following commands into it.


sudo add-apt-repository ppa:sun-java-community-team/sun-java6
sudo apt-get update
sudo apt-get install sun-java6-jre

Those should install it properly for you.

You might have to set your environment also, but I'm not sure.  If so, you can possibly put the following commands in the command line:

sudo update-java-alternatives -l

(note this will list the available java alternatives. It's for developers, but may work for you also. If it lists open-jdk and sun-java, then you'll put in the next command)

sudo update-java-alternatives -s java-6-sun

(note this *SHOULD* select the Sun Java JRE as your default, but as mentioned above, it's mainly aimed at developers--not end users, so your mileage may vary).

Hope this helps, and have a great day:)
Patrick.

---

