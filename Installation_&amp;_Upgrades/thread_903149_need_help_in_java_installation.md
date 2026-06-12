---
title: "need help in java installation ???"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by padam1989 on 2008-08-28
i have installed jdk1.6.0_07 manuallly on my desktop....
it is installed in /usr/lib/jvm directory....
now when i type java -version or javac on terminal,it reports a message that javac or java is note a command.........
the bottom line is that i am not able to compile or run my java programs.....
i am new to ubuntu...just migrated weeks before....
do i have to set the classpath like we used to do in windows....
If so pls help me to how to do it......
since i am new to ubuntu pls advice me a simple steps to configure java....

and also i tried sudo update-alternatives --config java.it report a message that no alternative is available.....

so pls pls help me to to run java on my ubuntu...because now i want to completely migrate to ubuntu from windows.Since i am java programmer,i want my java programs to run in ubuntu....

I ALSO WANT TO STATE THAT I HAVE GOT A UBUNTU 8.04.1 LTS DESKTOP EDITION..........

---

### Post by aysiu on 2008-08-28
Maybe this will help:
[http://www.psychocats.net/ubuntu/java](http://www.psychocats.net/ubuntu/java)

---

### Post by Sef on 2008-08-28
On 32-bit systems:

Applications > Add/Remove > Show: change to 'All Available Applications' > Search: Sun Java 6 > click on the top box > apply changes > apply > close

On 64-bit systems:

Applications > Add/Remove > Show: change to 'All Available Applications' > Search: OpenJDK > click on box > apply changes > apply > close

---

