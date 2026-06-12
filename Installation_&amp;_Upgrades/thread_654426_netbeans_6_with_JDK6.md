---
title: "netbeans 6 with JDK6"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by cunfuzd4 on 2007-12-31
I'm trying to install jdk6 w/Netbeans 6.  I used the sudo chmod +x  to make the .sh file executable and when I run it with sudo ./<filename> the installer starts then stops.  The text of the install run is:

Configuring the installer...
Searching for JVM on the system...
Preparing bundled JVM ...
Extracting installation data...
Running the installer wizard...

Then the terminal window goes back to the prompt and nothing else happens.  What am I doing wrong here?

---

### Post by kgriffin on 2008-01-01
Hi,
 
I just installed Netbeans 6 + Java 6 on gutsy, and this is how I did it.

I downloaded sun-java6-jre (run time)
                       sun-java6-jdk (for java devlopment)
                       sun-java6-bin (for run time) from Synaptic Package Manager [System -> Administration -> Synaptic Package Manager]

I also downloaded the fonts and plugins but you don't *need* them 

I then went to [ [COLOR="Red"]here[/COLOR] ]("http://download.netbeans.org/netbeans/6.0/final/") to download Netbeans 6, I went for "all" just because I was curious about all the extras.

I downloaded it to my Desktop, opened Terminal

```

cd ~/Desktop 

```

then ran the installer
```

sh netbeans6.0-linux.sh

```

no chmoding here :S

Hope that helps.

---

