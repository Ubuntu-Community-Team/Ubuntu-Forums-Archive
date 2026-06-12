---
title: "Is this set up for sun JDK? ...i dont think so, can u assist!"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by honey toast on 2010-03-05
can someone help me set my manually installed eclipse 3.5 to use my sunjdk 1.0.6.18 that i downloaded from the sun website?. Right now java -version, says this :

```

java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)


```I know i need to change my paths somehow, and sow I tried to insert this:

```

sudo echo "export JAVA_HOME=/usr/lib/jvm/jdk1.6.0_18/bin/java" >> /etc/profile
along with this...
sudo echo "export PATH=$PATH:/usr/lib/jvm/jdk1.6.0_18/bin" >> /etc/profile



```but the terminal only returns this...

```

bash: /etc/profile: Permission denied


```and so I manually went into profile and inserted the two paths up above in there and saved and still nothing happened. I tried the same thing with the bash.bashrc file to no avail. 


I don't know what all the talk is about some file called JAVA_HOME because I have never seen it, and I cannot find it anywhere on my file system hierarchy. 

when I sudo update alternatives --config i get this:

```

update-alternatives: warning: alternative /usr/lib/jvm/java-6-openjdk/jre/bin/java (part of link group java) doesn't exist. Removing from list of alternatives.
There are 1 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                  Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-sun/jre/bin/java   63        auto mode
* 1            /usr/lib/jvm/java-6-sun/jre/bin/java   63        manual mode


```
Does is look good or what? All i see is the jre, but I will be doing developing with my eclipse in Java and C, so I think I would need the JDK yes?...no? Any insight would be great.

---

### Post by darkod on 2010-03-05
Did you install the downloaded JDK? Also, I'm not sure what the difference is between downloaded from Sun website, but you have JDK in ubuntu repositories.

Either use Synaptic and search for sun-java6-jdk or just do in terminal:

sudo apt-get install sun-java6-jdk

That will take care of everything, including dependencies. After that you should have no problem making Eclipse use it.

---

### Post by honey toast on 2010-03-05
no i didn't install it through synaptic, instead, I went to the sun microsystems website and dl-ed from there. I guess I can try the synaptic, but i kinda wanted the new release. I've got the new release sitting in /usr/lib/jvm but i don't know how to configure it to work.

---

### Post by darkod on 2010-03-05
> **honey toast said:**
> no i didn't install it through synaptic, instead, I went to the sun microsystems website and dl-ed from there. I guess I can try the synaptic, but i kinda wanted the new release. I've got the new release sitting in /usr/lib/jvm but i don't know how to configure it to work.

My question was did you install it at all? Just downloading doesn't install it automatically, as far as I know.
If you didn't install it, Eclipse can't find it.

---

### Post by Mighty_Joe on 2010-03-05
Yea, there's a little more to the process than downloading the JDK.  Have a look  [at these instructions]("http://sites.google.com/site/easylinuxtipsproject/java").

---

### Post by honey toast on 2010-03-06
OK- I made the corrections that I wanted. :PThanks for posting that M. Joe. It was very clear and easy to follow. I'm going to close up the thread now.

---

### Post by protiss on 2010-03-15
Sorry if this is a little old - I just started learning Linux and this worked perfectly for me ... ([http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)).

However, I'm trying to actually understand what I do, in lieu of just doing what someone tells me to - so that maybe one day I won't have to research what to do.

Anyway, I downloaded and was able to extract the files properly, I just couldn't get my system to actually install (java -version still showing 6.15).  I understand all of the commands (moving the files, even the purpose of the chmod), however I'm having difficulty with letting the system know to use the new java version.....

[SIZE=3][COLOR=#000000][COLOR=#0000FF]sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_18/bin/java" 1.[COLOR=Black][SIZE=1]
[FONT=Verdana]
so I'm going to break down the (minimal) parts I understand, that way someone doesn't have to explain everything..

sudo - got it...

through the first operand, I'm pretty clear. I'm assuming the update-alternatives command is telling it it's not something it's going to find in one of the normal repositories, vice apt.

install "/usr/bin/java" - telling it the location to install?

"java" not really sure what this is about.  are we just letting the system know we're modifying software named "java" (don't overkill this, I know what java is, just asking if that's telling linux what it's supposed to be playing with).

"/opt/java/32/...."  - got it. directory we originally extracted to.

1 - no clue what this is for.

So basically, are we doing:
sudo update-alternatives --install "/usr/bin/[program]" "[linux-program-identifier]" "[location of extracted files]" X?

Where X= some number which I'm sure will be much more clear once someone responds?

Thanks in advance for the help.
[/FONT][/SIZE][/COLOR][/COLOR][/COLOR][/SIZE]

---

### Post by Mighty_Joe on 2010-03-16
Like every other command in a Unix system, you can type:
```
man update-alternatives
```
to get documentation:

```
DESCRIPTION
It is possible for several programs  fulfilling  the  same  or  similar functions  
to  be  installed  on a single system at the same time.  For  example, many 
systems have several  text  editors  installed  at once. . .
Debian's alternatives system aims to solve  this  problem.      

```

---

### Post by protiss on 2010-03-16
Yeah, I know the man command.  My apologies for thinking someone would actually be helpful - so glad I registered... So, if we can always just refer people back to the man command, why is the forum here?

"hey, I can't mount something" >>
"man mount" >>
"oh, thanks"

Maybe I need to check the Fedora forums lol.

---

### Post by Mighty_Joe on 2010-03-16
Have a look at: [How to ask questions the smart way]("http://catb.org/~esr/faqs/smart-questions.html")

---

### Post by GregBrannon on 2010-03-16
Considering that you said,

> However, I'm trying to actually understand what I do, in lieu of just doing what someone tells me to - so that maybe one day I won't have to research what to do.

Mighty_Joe's response was appropriate.  Your response was not, but we all have bad days.  Here's hoping that you're having a better one.

---

### Post by protiss on 2010-03-16
I understand his response was correct. That doesn't make it friendly or welcoming.  And the manual doesn't always answer everything.  Example (yes I know this doesn't belong in this thread but I doubt I'd get an answer even if I asked it).
 
That 'mount' comment from earlier wasn't by chance.  Trying to mount an .iso with windows files on it.
 
Doesn't matter if you -o loop it, it needs wine to run and the permissions are different under sudo/root than admin, so wine won't run it.  Supposedly from forums if you mount to /media/cdrom0 it'll let you use wine.  That doesn't work.  Manual doesn't help.  
 
Anyway, I'll just have to figure that one out on my own - just pointing out that the manual isn't always easy to understand and it doesn't always answer questions.  People (who have been doing this a long, long time) however, probably do understand, and probably could help, or explain it in a different manner.  So yes, his answer was great, and I've checked it out - I guess I had just always heard that linux was like a family of people who liked to help each other learn.  I guess, however, that I was somewhat mistaken.

---

