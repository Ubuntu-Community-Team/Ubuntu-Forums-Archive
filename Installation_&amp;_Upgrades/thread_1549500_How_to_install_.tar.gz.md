---
title: "How to install .tar.gz????"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by epsalas11 on 2010-08-09
I need some serious help i've been using ubuntu for two years now nd i still havent been able to figure out how to install programs that come in .tar.gz format. I know wat .tar.gz is. I just dont know how to install i get lost when ppl say to make a directory to where i save it o when ppl say "cd to directory" PLZ i need step by step instructions easy enough for a 3 year old to understand because i don't know anything about this stuff. The program im tryin to install is Netscape Navigator 9. And i have it in my desktop folder. I have found sum ppl that do have tutorials i just don't get them

---

### Post by TheStroj on 2010-08-09
Many tutorials on this:

[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

Ofcourse, where it says 'cd to something' it requires use of Terminal, I guess you got lost there.

---

### Post by flick on 2010-08-09
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Installing_a_package_from_source](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Installing_a_package_from_source)

---

### Post by epsalas11 on 2010-08-10
thanks guys but im still having trouble wen i go into terminal the commands is where it all goes wrong

---

### Post by oldos2er on 2010-08-10
Can you copy and paste the terminal output here?

---

### Post by snowpine on 2010-08-10
Sorry to be blunt my friend, but if you do not make a basic effort to read the documentation and understand the commands you're typing into the terminal, you are headed for disaster. Put yourself in the shoes of the people trying to help you, now tell me if statements like "the commands is where it all goes wrong" are going to get you the kind of help you're looking for?

Why not install applications from the Ubuntu Software Center? There are thousands of tested and trusted applications that can be installed with a simple point and click interface. :)

---

### Post by yunone on 2010-08-10
> **flick said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Installing_a_package_from_source](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Installing_a_package_from_source)

good link...thank you!!!

---

### Post by epsalas11 on 2010-08-10
i actually am trying to but believe me my friend i just dont understand it ive been tryin for months now to figure out how to install .tat.gz files nd i still cant. its not like im being lazy i just dont understand n e thing about it.

---

### Post by AlphaLexman on 2010-08-10
Generally, .tar.gz files are 'source code' files, and no offence here, but newbies may have more difficulties compiling from source code. I still struggle with compiling, with dependencies and all!

Really, if you don't understand it, we (the forums) can't explain it in a single post. 

My best advice is to install from the repo's until you figure everything out.

But to get you started...

Once the file is 'un-gzipped' into a directory, execute the following commands in a terminal:

```
./configure
make
make install
```

---

### Post by epsalas11 on 2010-08-10
ok so i extracted it desktop nd i entered the command given nd this is wat i got:


elvin@elvin-desktop:~$ navigator./configure
bash: navigator./configure: No such file or directory
elvin@elvin-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by dcollier on 2010-08-10
after you extract the file, you should read the readme file and it will tell you exactly how to run the application. first looking at the command that you were trying to run.

elvin@elvin-desktop:~$ navigator./configure 'sudo ./configure'
bash: navigator./configure: No such file or directory
elvin@elvin-desktop:~$ make 'you can't run make with out running ./configure'
make: *** No targets specified and no makefile found. Stop. 

The readme file on any program that you are trying to compile should always be your starting point before running the ./configure command

---

### Post by epsalas11 on 2010-08-12
i checked the read me nd all it reads is:

For information about installing, running and configuring Navigator
Navigator, refer to: [http://browser.netscape.com/](http://browser.netscape.com/)

thats it nd wen i go to the website it says that they will no longer provide support for the program

---

### Post by oldos2er on 2010-08-12
Would you mind explaining why you want to run Netscape Navigator? It's ancient history as far as computer programs go, and frankly I'd be concerned about possible security issues with it.

---

### Post by epsalas11 on 2010-08-12
sum websites give me hassles nd dont support mozilla or chrome

---

### Post by oldos2er on 2010-08-12
Which sites? What exactly do you mean by "hassles"? Please post any error messages.

---

### Post by epsalas11 on 2010-08-13
just job sites im 17 nd ive been lookin nd several sites require ie or netscape i was at a lost for words wen i saw netscape on that list but yea they require ie 7 or newer or netscape navigator

---

### Post by lykeion on 2010-08-13
My advice is to use a user-agent switcher with firefox.
An example is this add-on:
[https://addons.mozilla.org/en-US/firefox/addon/59/](https://addons.mozilla.org/en-US/firefox/addon/59/)

With this add-on you can set the user-agent to IE or Netscape, and avoid websites hassling with you.

Hope this helps...

---

### Post by epsalas11 on 2010-08-13
WOW the add-on really worked. Thanks

---

