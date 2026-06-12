---
title: "Blurred text in Jdownloader, java problem?"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rado3105 on 2010-04-06
Hi I have installed lucid, I installed openjdk enviroment to run jdownloader(which java based program for downloading) and there is blurred text inside. It was ok using 9.10. And jdownloader is in the same version.
[IMG]http://i40.tinypic.com/2vxnkau.png[/IMG]

---

### Post by -siGGi- on 2010-04-06
```
sudo apt-get install sun-java6-jre
```
```
sudo update-java-alternatives -s java-6-sun
```
```
wget http://212.117.163.148/jd.sh
```
```
sh jd.sh
```

---

### Post by Speque on 2010-04-06
I had similar problems with another program. Use Sun JRE instead of OpenJDK and the problem will be solved.

---

### Post by rado3105 on 2010-04-06
Thanks it seems that it is not in my repositories. sun-java6-jre.

---

