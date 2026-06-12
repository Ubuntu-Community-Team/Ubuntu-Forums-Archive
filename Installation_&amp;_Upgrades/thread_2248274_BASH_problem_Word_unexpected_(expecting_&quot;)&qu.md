---
title: "BASH problem Word unexpected (expecting &quot;)&quot;)"
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by dylan0005 on 2014-10-13
Hello! I've been trying to run a portable aplication (Skype) on my **Lubuntu OS** but It's been dificult because every time I try to run it in the terminal it doesn't work, I put the following lines:

```
 
sudo chmod 777 Skype_2.1.0.81
sh Skype_2.1.0.81

``` 

It shows an error : **Word unexpected (expecting ")")** and if I try with **./Skype_2.1.0.81** instead of** sh Skype_2.1.0.81** shows : **Permission denied**.
If someone could help me with this I would appreciate it!

---

### Post by steeldriver on 2014-10-13
if you are running it using sh that would be a DASH problem rather than a BASH problem - if it really is a bash script (and you can't run it using ./Skype_2.1.0.81, perhaps because it is located on a filesystem that doesn't support Unix permissions - such as an external USB), you should run it using 'bash Skype_2.1.0.81'

---

### Post by dylan0005 on 2014-10-13
@steeldriver Yes you're right, I'm trying to running it from a USB so I tried with the command you said: **bash Skype_2.1.0.81** BUT the system showed another message : [B]It cannot execute the binary file. 
[/B]
Do you haveany suggestions?

---

### Post by steeldriver on 2014-10-13
What type of executable is it? can you  post the outputs of

```

file Skype_2.1.0.81

uname -a

```

---

### Post by dylan0005 on 2014-10-13
@steeldriver here are the outputs
```

file Skype_2.1.0.81
Skype_2.1.0.81: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, BuildID[sha1]=979b03ecd4f375112b8d3da2f4e2f1e32029dcc5, stripped

uname -a
Linux dylan-AsusPc 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux


```

---

### Post by sudodus on 2014-10-14
What happens if you try to run Skype directly (without sh or bash)?

```
Skype_2.1.0.81
```

You can also try if it works with the generic command (which used to work, and still works for me with the version installed via the repositories)

```
skype
```
[I]
[COLOR=#696969]Edit:[/COLOR][/I][COLOR=#696969]

I get a working Skype version via the repositories (from the Software Center, Synaptic or this command line)

```
sudo apt-get install skype
```

in my Ubuntu 12.04.5 LTS it installs version 4.3 (in accordance with Vladlenin5000's advice)

```
skype -version
Skype 4.3.0.37
```[/COLOR]

---

### Post by dylan0005 on 2014-10-15
Unfortanely running it directly doesn't work too, the system showed me another message : ·"[I]the command was not found"
 
[/I]This issue is taking so much time than I had expectedto[I]. 
[/I]

---

### Post by Vladlenin5000 on 2014-10-15
Skype 2.1 doesn't work now even if you eventually succeed in running that scrip so why bother?. And this
```
Skype_2.1.0.81: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for [COLOR=#ff0000]GNU/Linux 2.6.15[/COLOR], BuildID[sha1]=979b03ecd4f375112b8d3da2f4e2f1e32029dcc5, stripped
```
tells me it's coded for a very old kernel version.

---

### Post by nerdtron on 2014-10-16
Don't run it with sh or bash since the file isn't created for bash. Just run the file as it is intended to:
```
 ./Skype_2.1.0.81 
```

(be sure to cd in to the directory first)

---

### Post by Vladlenin5000 on 2014-10-16
Again, no Skype version other than 4.3 currently works. Even if someone manages to run that old script it'll be nothing more than an interesting exercise.

---

### Post by sudodus on 2014-10-17
I get a working Skype version via the repositories (from the Software Center, Synaptic or this command line)

```
sudo apt-get install skype
```

In my Ubuntu 12.04.5 LTS it installs version 4.3 (in accordance with Vladlenin5000's advice)

```
skype -version
Skype 4.3.0.37
```

---

### Post by dylan0005 on 2014-10-17
Thank you all for your responses! Well @Vladlenin5000 I didn't know about the old kernel and version of the program. Actually it's an exercise for running those scripts. I'm going to try to run another script and I hope it doesn't show the same inconvenient. It's a test.

---

### Post by dylan0005 on 2014-10-27
I didn't know about the old kernel version; though I don't have any current aplication for the latest versions of Lubuntu or Ubuntu.
I mean Portable Apps like The version of skype I've been trying to run

---

### Post by sudodus on 2014-10-27
Please explain what you want!

Do you want a Skype version on a pendrive? Do you want it portable between different computers or operating systems? Would it be OK with a bootable USB drive, where you have installed Skype? Or must it work, when plugged into a running operating system?

Some of these options are easy, some harder (and some maybe impossible).

---

### Post by dylan0005 on 2014-10-28
Well it's very simple, it's not about skype, it boils down to this: _ Running Portable Apps on Lubuntu_ because it seems like it can't run any portable app in the terminal even if the permissions for it are given, the system almost always throws an error.

---

### Post by sudodus on 2014-10-28
Maybe the apps are 'not portable enough'. We have found out why that version of Skype does not work. What other apps have you tried? What systems were they made for? Can we expect them to work with this 32-bit version of Lubuntu for i686 architecture? 

```
uname -a
Linux dylan-AsusPc 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux
```

Please describe with another example, and we can explain what is wrong and if/how another version of that application program can work :-)

---

### Post by dylan0005 on 2014-10-30
I've tried the Portable Apps from_ PortablelinuApps.org _especifically *Skype, Spotify and LibreOffice* and none of them worked. It Always showed a message like : **Syntax Error: word unexpected (epecting ")")** So I'm starting thinking that it might be a LUBUNTU OS problem instead of the applications because in Ubuntu those ran in a normal way...

---

### Post by sudodus on 2014-10-31
I browsed the documentation at [http://www.portablelinuxapps.org/](http://www.portablelinuxapps.org/) Now I see what you mean :-)

So these portable apps work in Ubuntu but not in Lubuntu. Is it the same version and architecture, for example 14.04.1 LTS and 64 bits in both cases? In that case there must be some help program under the hood, that comes with different versions in Ubuntu and Lubuntu. ***I don't know what it could be, but hope that someone will recognize the problem and help us understand it***.

---

### Post by dylan0005 on 2014-10-31
I see... I get what you're saying. Well Lubuntu is based on Ubuntu (Besides, it's the latest version of Lubuntu) so I dare say that those applications must run without any inconvinient in both systems. From what I've seen and proven the normal programs that you have to install and come for Ubuntu versions after installation those don't throw errors and just run normally.
Anyway as you were saying there's something we are missing but hopefully someone will help us. I appreciate your help* @sudodus*

---

### Post by bapoumba on 2014-11-01
I have tried with AppImageAssistant. Was getting all the same errors as above. For ex :

```
bapoumba@bapoumba-utopic:~/Desktop$ dash AppImageAssistant\ 0.9.3
AppImageAssistant 0.9.3: 1: AppImageAssistant 0.9.3: Syntax error: word unexpected (expecting ")")
```

Made the script executable for owner and group (was not executable) and got it to launch without the error. But I do not know what to do with this app, I do not even know what i is supposed to be doing. Once it is happy with the AppDir, I only can go back or cancel. Lubuntu 14.04. [COLOR="#FF0000"]Edit, sorry, my mistake. I was on my 14.10 install.[/COLOR]

---

### Post by sudodus on 2014-11-01
> **bapoumba said:**
> I have tried with AppImageAssistant. Was getting all the same errors as above. For ex :

```
bapoumba@bapoumba-utopic:~/Desktop$ dash AppImageAssistant\ 0.9.3
AppImageAssistant 0.9.3: 1: AppImageAssistant 0.9.3: Syntax error: word unexpected (expecting ")")
```

Made the script executable for owner and group (was not executable) and got it to launch without the error. But I do not know what to do with this app, I do not even know what i is supposed to be doing. Once it is happy with the AppDir, I only can go back or cancel. Lubuntu 14.10.

Thank you *bapoumba*  :-)

So the solution is to make  the script executable for owner and group. At least the error output
```
Syntax error: word unexpected (expecting ")")
``` should disappear that way.

---

### Post by bapoumba on 2014-11-01
Sorry I made a mistake in my previous post as you might guess from my prompt. I was in the 14.10 install.

That said, I am very surprised this could be the solution. Seasoned script people posted in here, I know nothing about all this. Thought about this while trying to find bash/dash differences between ubuntu and lubuntu and more info about the error. The error is already documented (sorry, I closed the window where I had links) and sounds like common for cross arch compiled scripts where some options are set up wrong. Once again, I know nothing about that :)

---

### Post by sudodus on 2014-11-01
I must admit, that I did not notice the utopic prompt, so thanks for making it clear. So now we know that things should work in Lubuntu 14.10.

---

