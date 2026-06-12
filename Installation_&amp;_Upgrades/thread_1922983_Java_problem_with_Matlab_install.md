---
title: "Java problem with Matlab install"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by jordantash on 2012-02-09
Hi,

I've installed xubuntu (I really like Xfce) on two computers, one 32 bit and one 64 bit. I really need Matlab on both machines. After downloading all the appropriate files, and executing the "./install" command in the download directory, I get the message:

Exception in thread "main" java.lang.NoClassDevFoundError: 32
Caused by: java.lang.ClassNotFoundException: 32

It's the same for both computers. I tried downloading and installing Java straight from java.com, and using OpenJDK's JRE 6 and 7. Still no luck, and I'm pretty much out of ideas. I'd really appreciate some help on this one.

Thanks,
Jordan

---

### Post by raja.genupula on 2012-02-09
[http://ubuntuforums.org/showthread.php?t=1837916](http://ubuntuforums.org/showthread.php?t=1837916)

---

### Post by jordantash on 2012-02-09
Sorry, I still don't quite understand. The person in that thread is trying to run a .jar file I think. Could you please elaborate a bit?

---

### Post by raja.genupula on 2012-02-10
[http://ubuntuforums.org/showthread.php?t=781078&highlight=compiz+matlab](http://ubuntuforums.org/showthread.php?t=781078&highlight=compiz+matlab)

---

### Post by jordantash on 2012-02-10
Yeah, I have seen that thread. Nobody there mentioned having a similar problem, and I didn't want to revive something several months old. I followed jweber's guide when I first started having trouble, but I've always just gotten the same "NoClassDefFoundError: 32" error.

I've also tried installing with the -javadir argument to point directly to my java install. No luck there either.

---

