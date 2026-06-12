---
title: "BackTrack 4 Tools to Ubuntu ERROR HELP"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by wmfd_2003 on 2010-11-06
I am following a tutorial on this link...[http://hakblog.co.uk/2009/11/26/add-backtrack-4-tools-to-ubuntu-tutorial/](http://hakblog.co.uk/2009/11/26/add-backtrack-4-tools-to-ubuntu-tutorial/)

When I get to: 
**3. Build your package list**
 [B](note you may need to sudo apt-get links if you do not have it installed)
[/B]
 links -http-proxy myproxyserver.com:8080 -dump  [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/ | awk ‘{print $3}’ |  grep -i deb | cut -d . -f 1 > backtrack.txt


I get this error:


root@hacker-mobile:~# links -http-proxy myproxyserver.com:8080 -dump [http://repo.offensive-security.com/dist/bt4](http://repo.offensive-security.com/dist/bt4) binary/ | awk ‘{print $3}’ | grep -i deb | cut -d . -f 1 > backtrack.txt
awk: 1: unexpected character 0xe2
awk: line 2: missing } near end of file
Unknown option binary/
I tried it as $ and as #, that made no difference. I just showed * bc it was what I had last tried...plz exlain to me what it is saying I need to correct

---

### Post by P4man on 2010-11-06
Try replacing the inverted comma's with regular apostrophes
so

```
'{print $3}'
```
instead of
```
&#8216;{print $3}&#8217; 
```

(well I cant even paste those correctly here as you have them). Probably an issue with the blog software the guy uses which replaces those apostrophes.

---

