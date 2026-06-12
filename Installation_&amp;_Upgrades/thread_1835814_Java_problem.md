---
title: "Java problem"
date: 2011-08-30
forum: Installation &amp; Upgrades
---

### Post by Metalbot on 2011-08-30
I've installed the following from the software center:
OpenJDK JAVA 6 runtime
IcedTea Java 6 webstart.
I also installed Geany.

However, I cannot compile my java code. It gives me this message.
 /bin/sh: javac not found.
I've read some threads regarding this and they say i need the javac executable to compile my code. But i don't know what i'm supposed to do. Please help.

Thank you.

---

### Post by lykeion on 2011-08-31
The java compiler (javac) is in the package OpenJDK Development Kit (openjdk-6-jdk). After installation you can safely remove package OpenJDK Java 6 Runtime and Web Start.

---

### Post by Metalbot on 2011-09-08
that doesn't solve the issue. The compiler still doesn't identify the 'javac' command.

---

### Post by Metalbot on 2011-09-08
i found the "javac" file in a computer search.

 It's location is: /media/system/Program Files/Java/jdk1.7.0/bin 

I know it needs to be in bin/sh for my programs to run.
But when i open "bin" in my Filesystem, there is no subfolder called "sh". There's a "link to exectable" file called "sh". What do i do to set this right? Please answer.

Thank you.

---

### Post by lykeion on 2011-09-10
The Java path you are referring to seems to be a mounted Windows partition.

Step-by-step to setup compiling Java in Geany:
Note: This is Ubuntu 10.04, it might differ some on later Ubuntu versions.

1) Start a terminal (Applications > Accessories > Terminal)
2) Install package OpenJDK Development Kit (openjdk-6-jdk) with this command: ```
sudo apt-get install openjdk-6-jdk
```
3) Verify that you can execute Java compiler (javac) in terminal, with this command (it should output the installed version): ```
javac -version
```
4) Start Geany (I'm using version 0.20)
5) Enter this code:[PHP]class HelloWorld {
	public static void main(String[] args) {
		System.out.println("Hello world");
	}
}[/PHP]
6) Save the file as HelloWorld.java
7) Compile it in Geany: Build > Compile (F8)
8) Run it in Geany: Build > Execute (F5)

---

### Post by Metalbot on 2011-09-19
_@ _[lykeion]("http://ubuntuforums.org/member.php?u=102981") : Many thanks. Your suggestion was perfect. :D

---

