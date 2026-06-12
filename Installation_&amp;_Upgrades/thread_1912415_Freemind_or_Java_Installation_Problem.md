---
title: "Freemind or Java Installation Problem?"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by Scipio_Publius on 2012-01-20
Hello, I installed java 6 via these instructions

[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

When I try to run freemind I get this error

```
freemind
[warning] /usr/bin/freemind: No java runtime was found
[error] /usr/bin/freemind: Unable to find an appropriate java runtime. See java_wrappers(7) for help

```

My java version is

```
java -version
java version "1.6.0_30"
Java(TM) SE Runtime Environment (build 1.6.0_30-b12)
Java HotSpot(TM) Server VM (build 20.5-b03, mixed mode)

```

The freemind documention seems to indicate this is a good version.  Im kinda stumped as to where to look next for troubleshooting.

Any idea would be appreciated.

---

### Post by lykeion on 2012-01-20
How did you install freemind? It's in the universe repositiories. Make sure it's enabled and install freemind with Synaptic, Ubuntu Software Center or with apt-get:

sudo apt-get install freemind

---

### Post by Scipio_Publius on 2012-01-20
I actually tried all three of those methods.  Still no joy.  I thought perhaps because of the way I installed the JRE it can't find it.

---

### Post by lykeion on 2012-01-21
I use the same script from duinsoft.nl to install the latest Java JRE and I have no problem with installing and running freemind.
I'd suggest you to read the instructions on the duinsoft webpage and use the Repository method, as it will remove any previous installed out-of-date sun-java6 installation you might have.

---

