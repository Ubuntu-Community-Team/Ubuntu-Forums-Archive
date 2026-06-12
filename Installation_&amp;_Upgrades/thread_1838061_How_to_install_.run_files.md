---
title: "How to install .run files?"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by bholzer on 2011-09-02
I'm trying desperately to install a .run file on natty, but nothin I'm doing seems to be working. 

Thanks for the help!

---

### Post by sum1nil on 2011-09-02
To install you should just have to do:
sh ./<name of package>.run . However, you may have to chmod beforehand by using 'sudo chmod 755 <name of package>.run to allow it to run as an executable. 

:popcorn:

---

### Post by Hakunka-Matata on 2011-09-02
```
sudo bash <packagename>.run     or .sh
# bad command - useless
```Above code useless.............



use this:
```
sh someFileYouWant.run
```
See [this]("http://www.linuxforums.org/forum/gaming-multimedia-entertainment/35202-installing-run-files.html") link to forum thread on subject

---

