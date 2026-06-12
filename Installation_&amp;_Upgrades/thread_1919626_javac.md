---
title: "javac"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by uburudu on 2012-02-03
Hello !

I have problem with my java instalation, i can compile java code with Eclipse IDE but i cannot compile on terminal ( with javac ) ... i couldn't find any solution on older posts and i'm a bit confused...
i think i have messed up my system :S

related commands & output:

```
[COLOR=Navy]username$[/COLOR] lsb_release -r
Release:    11.10
```ubuntu 11.10 (x64)
.

```
[COLOR=Navy]username$ [/COLOR]java -version
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10.1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)
[COLOR=Navy]username$[/COLOR] 
```.

```
[COLOR=Navy]username$[/COLOR] [COLOR=DarkRed]javac
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.6-jdk
 * gcj-4.5-jdk
 * openjdk-7-jdk
Try: sudo apt-get install <selected package>[/COLOR]
[COLOR=Navy]username$[/COLOR] 
```.

```
[COLOR=Navy]username$[/COLOR] sudo apt-get install openjdk-6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-6-jdk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[COLOR=Navy]username$[/COLOR] 
```

.

```
trying to compile with Geany i get the msg:

javac "HelloWorld.java" (in directory: /home/[COLOR=Navy]username[/COLOR])
Compilation failed.
/bin/sh: javac: not found


```

.

```

[COLOR=Navy]username$[/COLOR] cat HelloWorld.java 
class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
[COLOR=Navy]username$ [/COLOR]

```

---

### Post by doobrie on 2012-02-03
It looks like you have javac already installed.  If you execute

$ which javac

Does it show you the installation path?

I've found java 7 to be better.  Have you tried using that version?

---

### Post by uburudu on 2012-02-03
```
username$ which javac
username$ 

```it doesn't give me any output

but with " $ locate javac " i can see a path " /usr/lib/jvm/java-6-openjdk/bin/javac "

-

i tried 
sudo apt-get openjdk-7-jdk
yesterday with  the same results

---

### Post by uburudu on 2012-02-03
not sure if there is a better solution

but i made manually a javac link at "/usr/bin/" dir and it [U][B][COLOR=Black]fixed my problem[/COLOR]
[/B][/U]
```
username~$ sudo ln -s /usr/lib/jvm/java-6-openjdk/bin/javac /usr/bin/javac
```


[I]thnx for the reply @doobrie, and my friend MITSARAS !

KOSEOS!
bb
[/I]

---

### Post by doobrie on 2012-02-03
For some reason you have the compiler installed, but it wasn't in your path (hence making the link worked).

Making the link is a good solution.

---

