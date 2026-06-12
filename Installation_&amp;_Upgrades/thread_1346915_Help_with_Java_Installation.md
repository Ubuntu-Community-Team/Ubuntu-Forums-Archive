---
title: "Help with Java Installation"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by immortalgeek on 2009-12-05
Hello,

I am a new Linux and Ubuntu user. I downloaded SUN jdk 6 from sun website and installed int in /home/<my username>/SDK folder. when i execute the javac command from the terminal I get the following error:


:~/SDK/jdk/bin$ javac
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
javac: command not found

Can anyone please suggest how can I get this working.

Thanks in advance for your advice!

~immortal

---

### Post by immortalgeek on 2009-12-05
I think I figured out how to run. Insted of $javac i gave $./javac and it worked!

Let me know guyz if there is a better way to do this.

---

