---
title: "Gutsy-another Update that didnt!"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by KEE on 2008-10-29
every time i try to update when i see the updater icon show up on task bar i get this ....=-(

```
  this package is an installer package, it does not actually contain the JDK documentation. YOu will need to go download one of the archives:

jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).

http://java.sun.com/javase/downloads/

now and downlaod. The file should be owned by root. root and be copied to /tmp.
[Press Return to try again, 'no' + return to abort]
```

not sure what to do i have that file in desktop, and i tried to install it but the most i can do is extract it. this is my second post on this and no replies =-( still the update shows up and yet i cant update anything =-( for more details check my old post =-( [http://ubuntuforums.org/showthread.php?t=959202](http://ubuntuforums.org/showthread.php?t=959202)

---

### Post by Saul Hudson on 2008-10-30
I had the exact problem, and I managed to solve it using your previous post!
So I hope I can help you out in return :-)

I downloaded the "jdk-6-doc.zip" file using the link on the other post:[http://www.filewatcher.com/m/jdk-6-doc.zip.54898268.0.0.html]("http://www.filewatcher.com/m/jdk-6-doc.zip.54898268.0.0.html")

...to my desktop, just to make it easier.

Go into your terminal and get into your Desktop folder

then type:

```
cp jdk-6-doc.zip /tmp
sudo chown root:root /tmp/jdk-6-doc.zip

```

You might want to navigate around a bit in between, getting into the correct folder, but that's essentially it. I know I've only repeated what "partyboi2" said, so any credit should go to him, but you didn't seem to understand what to do with the file. You just do that :-)

---

