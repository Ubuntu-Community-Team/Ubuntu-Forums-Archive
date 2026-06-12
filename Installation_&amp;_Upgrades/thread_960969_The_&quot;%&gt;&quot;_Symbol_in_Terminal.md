---
title: "The &quot;%&gt;&quot; Symbol in Terminal"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by Krazeel on 2008-10-27
Hello,

I would really appreciate some help with the following:

-In a list of instructions to install apache2 and php5 I was instructed to do this:
[LIST=1]
[*]Get the files "httpd-2.2.10.tar" and "php-5.2.6.tar"
[*]Move the files to the directory "/usr/src"
[*]Then execute these commands in Terminal in order to unzip the file:

[COLOR="Blue"]%>gunzip httpd-2.2.10.tar.gz[/COLOR]
[/LIST]
At this point I had some extra steps to do, which I had to find out myself just to make the commands work. I had to specify the path of the .gz and access as root - with sudo. And most importantly, I had to remove this "%>" symbol. The symbol repeats in the following commands and even further:

[INDENT][COLOR="Blue"]%>tar xvf httpd-2.2.10
%>cd httpd-2.2.10
%>./configure --enable-so [other options]
%>make
%>make install[/COLOR][/INDENT]

I couldn't succeed with the preceding commands, so first of all, I would like to ask what can the "%>" symbol possibly stand for.
:)
Thank you.

---

### Post by mcallenSchmee on 2008-10-27
That is just to show that the commands are entered at the terminal, you don't type them, they are not part of the command. You might also see $ used instead.

---

### Post by cariboo on 2008-10-27
Is there a reason why you are not installing the versions that are in the repositories?

Jim

---

### Post by Krazeel on 2008-10-28
Thanks mcallenSchmee and Jim for the quick response. 

[INDENT][I]"Is there a reason why you are not installing the versions that are in the repositories?

Jim"[/I][/INDENT]

I installed xampp for linux at first, then it turned out I did wrong, so I had to follow the instructions step by step just to be on the same track. And it's not the easiest way for me to proceed, but the instructions included these following prerequisites:
[LIST]
[*]To have Perl, Bison, Flex and an Ansi-C compiler - I'm not sure I got the last one - installed.
[*]Configure some lines in both php and apache configuration files.
[/LIST]
I'm starting from scratch in this topic and that's why I prefer to be delicate with this.

I will be posting again in the same thread if I have some problems I'm not able to solve.

Thanks again!

---

### Post by Krazeel on 2008-10-28
Hello,

I'm stuck! I wrote these commands:

-sudo gunzip /usr/src/httpd-2.2.10.tar.gz [COLOR="DeepSkyBlue"]- worked[/COLOR]
-tar xvf /usr/src/httpd-2.2.10.tar [COLOR="red"]- worked?[/COLOR]:confused:

In the second command the output had many lines, and every line began with "httpd-2.2.10/"

Then I had to write "cd httpd-2.2.10", then "make" and "make install". I wrote the previous lines and the commands "make" and "make install" didn't work. 
So what I don't understand is, first, where is the "httpd-2.2.10/" located -and by the way I searched the file system and there were no folders with such name- second, what the "xvf" part means in the "tar" command, and third how would I have to write the "cd"command to make this work.

Thanks for any help ;-)

---

### Post by zvacet on 2008-10-28
Command **tar xvf httpd-2.2.10** should make** folder** named **httpd-2.2.10** and command **cd httpd-2.2.10** just telling you to go inside of that folder.

---

### Post by Krazeel on 2008-10-28
Ok, from my understanding, I would be able to do the most of the process without going into the command line, just by gunzipping, untarring and going into the directory. Now what I fail to see is how would I achieve the "make" and "make install" part. 
Going back to the command line version, I think the "tar xvf" command worked as intended, but I couldn't find the folder. 
Even though I continued with "[COLOR="RoyalBlue"]cd usr/src/httpd-2.2.10[/COLOR]" and then "[COLOR="RoyalBlue"]make[/COLOR]", "[COLOR="RoyalBlue"]make install[/COLOR]". 
After typing "[COLOR="RoyalBlue"]cd usr/src/httpd-2.2.10[/COLOR]" the output was: "[COLOR="RoyalBlue"]username:~/httpd-2.2.10$[/COLOR]", 
after "[COLOR="RoyalBlue"]make[/COLOR]": "[COLOR="RoyalBlue"]make: *** No targets specified and no makefile found.  Stop.[/COLOR]" and after "[COLOR="RoyalBlue"]make install[/COLOR]", the output was: "[COLOR="RoyalBlue"]make: *** No rule to make target `install'.  Stop.[/COLOR]"
This isn't the output I'm looking for, so I'm still lost.

Anyway, I'm ashamed for not knowing how to solve this issue and I would like to excuse myself if I'm asking a lot. I'm a complete starter and I appreciate your time helping me.

---

### Post by zvacet on 2008-10-29
Once you are inside of usr/src/httpd-2.2.10 you should run these commands
[B]
%>./configure --enable-so [other options]
%>make
%>make install[/B]

---

### Post by Krazeel on 2008-10-29
After running this line: ./configure --enable-so (the [other options] part was unnecessary)inside the directory, the output had about 20 lines. The interesting part of the output was in the last lines: 
[INDENT][COLOR="Blue"]APR Version: 1.3.3
checking for chosen layout... apr
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr[/COLOR][/INDENT]
Now, I figured out it had something to do with gcc compiler. I ran synaptic to check if I had it installed and then I went to [the apache installation docs for linux]("http://httpd.apache.org/docs/2.2/install.html#page-header"), and I checked the requirements: 

[I]ANSI-C Compiler and Build System
    Make sure you have an ANSI-C compiler installed. The GNU C compiler (GCC) from the Free Software Foundation (FSF) is recommended. If you don't have GCC then at least make sure your vendor's compiler is ANSI compliant. In addition, your PATH must contain basic build tools such as make.[/I]

Now, in the last sentence "*your PATH must contain basic build tools such as make*", I don't know what "PATH" is and how I would have to enable the "make" tools. 
I hope it won't get much harder than this... ](*,)

---

### Post by zvacet on 2008-10-29
Do you have **build-essential** installed?If not install it from synaptic.

---

### Post by Krazeel on 2008-10-30
I followed the instructions from the Apache Httpd website and finally I had success. Now I'm facing problems with the apache configuration, but this isn't concerned with this thread. 
Anyway, thanks to all of you who helped me.\\:D/

---

