---
title: "Ubuntu 12.04 Chrome Java Plugin"
date: 2012-11-03
forum: Installation &amp; Upgrades
---

### Post by hmartine on 2012-11-03
Google Chrome does not detect java. I know this topic has been post everywhere, but I try their suggestions and it does not work. I need your help to know if there is anything I am doing wrong or anything I have not done yet.
This is what I have and what I have done
Ubuntu 12.04 recently installed
Java(TM) SE Runtime Environment (build 1.7.0_09-b05)
Google chrome Version 22.0.1229.94.
I also have firefox 16.0.2, and JAVA works fine there (using IcedTea pluging)

What I have done, 
I installed Java from the terminal
Then Icedtea plugin, also from the terminal, at this point java started working on firefox, which makes me think Java is working fine
I searched for the java lib using the command (find / -name libjava.so 2> /dev/null)
once it founded the lib I created a link of the "libnpjp2.so" to the chrome plugins folder using the following command "sudo ln -s /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnpjp2.so /opt/google/chrome/plugins/"
It did the link in the folder, but still when I go to Java to test, using the chrome browser, java does not work.

Any suggestions?

Thanks a lot

---

### Post by Tranas on 2012-11-03
Install default-jdk using Synaptic

works for me. ymmv

---

### Post by critin on 2012-11-03
In chrome 'Current Settings', are all sites allowed  to run JavaScript?

Did you install openjdk-7-jre?  It should be in Software Center.

---

### Post by kingpioneer on 2013-04-06
The best solution I found, (none of these suggestions worked for me), is as followings:
First install Icedtead pluging by:

[LIST]
[*]1) sudo apt-get install **icedtea-7-plugin**
[/LIST]

Then in your chrome browser go to:

[LIST]
[*]2) chrome-> Settings-> Show Advanced Settings-> Privacy then click on
[*]Content Settings -> Plug-ins then click on Disable Individual Plug-in
[*]3) Disable both "**IceTea-Web Plugin**" and "**Java(TM)**"
[*]4) Restart the browser.
[*]5) chrome-> Settings-> Show Advanced Settings-> Privacy then click on
[*]Content Settings -> Plug-ins then click on Disable Individual Plug-in
[*]6) Enable **only** "**IceTea-Web Plugin**"
[*]7) Enjoy !
[/LIST]

---

