---
title: "frostwire crashes on start up."
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by peterbug on 2007-04-12
I've looked through other posts but can't find a solution to my problem. I installed frostwire and java (properly) but when I try to run frostwire the start up screen appears and then stays there until I reboot my computer. Why isn't frostwire loading?

---

### Post by taurus on 2007-04-12
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
java -version
```
And try to start frostwire from a terminal in case there is an error message.

```
frostwire
```

---

### Post by peterbug on 2007-04-12
bug@bug:~$ java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)


and..

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading FrostWire:

and it stays like that.

---

### Post by taurus on 2007-04-12
How did you install frostwire, by hand, with synaptic, or with 3rd party app?

---

### Post by peterbug on 2007-04-12
tryed using automatix but that wouldn't work so instead I went to forstwire.com downloaded it there and then I used "gdebi 0.1.6ubuntu1" to install frostwire.

---

### Post by peterbug on 2007-04-12
help, anyone?

---

### Post by Franscisco on 2007-04-13
I have the same problem, if you figure that out, please post it the way you did it, so it will be very helpful.

---

### Post by microsoft92sucks on 2007-04-15
Same problem here wats up with that.... some1 please help

---

### Post by microsoft92sucks on 2007-04-15
I found a post saying how to do it just follow this it worked 4 me.
"if you go to synaptic package manager ...sun-java6-jre and sun-java6-bin should be available in the repositories ...if not then go to "settings ...repositories ...internet updates" and enable backports ...reload and do a search for java6 and you should then be able to install it ...if it's still not showing there go to terminal and do
Quote:
sudo gedit /etc/apt/sources.list
at the end of that text file add...
Quote:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
...go back to synaptic package manager and then java 6 should be available. I personally uninstalled java 5 first ...don't know if it matters.

after you have java 6 installed go back to terminal and type...
Quote:
sudo update-alternatives --config java
...this will list all java virtual machines installed and allow you to choose the default ...java 6 of course

worked for me when xgl/beryl wouldn't allow frostwire to open ...hope this helps"

---

### Post by ==[ VNMS1 ]== on 2007-04-29
Hi there,
Firstly, I'd like to thank you for solving this rather tedious headache. As a complete noob to linux, I was starting to scratch my head at this tedious endeavour of finding a LimeWire clone that actually WORKED! Fantastic. Thanks heaps.

---

