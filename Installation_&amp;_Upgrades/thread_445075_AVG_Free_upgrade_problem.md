---
title: "AVG Free upgrade problem"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by Bablefish on 2007-05-15
I tiried to install AVG Free Anti Virus program Linux version, by the way I used the .deb file and it installed fine. My problem involves updating the software and I need and expert in command lines. I used the documentation that goes with it which can be found at [http://free.grisoft.com/doc/5390/lng/us/tpl/v5](http://free.grisoft.com/doc/5390/lng/us/tpl/v5) and in the terminal I typed avgscan -register which I hoped would allow me to to this. But all I got was the serial and not much else. I know I screwed up some where but I can't quite figure out where. Any suggestions?

---

### Post by mikewhatever on 2007-05-15
The command line option for AVG update is 
> sudo avgupdate -o

---

### Post by Bablefish on 2007-05-15
That really wasn't it, after checking it again it is asking me for a valid license number. Or how else can you explain when I hit the update icon when the program is running 

Update progess failed. Reason, sorry you do not have premission to exicute

---

### Post by merlinus on 2007-05-15
You have to be running as root in order to update avg, and in order to do that, you open a terminal window and enter the command given by a previous poster:

sudo avgupdate -o  

Press <Enter>

It will then ask for your password.  Type it in, Press <Enter>, and the update files will begin downloading.

BTW, the o in -o is a lowercase o, not a zero.

-merlin

---

### Post by mikewhatever on 2007-05-15
> **Bablefish said:**
> That really wasn't it, after checking it again it is asking me for a valid license number. Or how else can you explain when I hit the update icon when the program is running 

Update progess failed. Reason, sorry you do not have premission to exicute

Actually, the free version does not ask for a license number. Have you got the right file? Have you tried the command line option?

---

### Post by Bablefish on 2007-05-16
Thanks Merlinus that did the trick

---

### Post by Chappy7777 on 2007-05-16
I don't understand why you are concerned about Viruses in the 1st place. Who writes viruses to attack Linux? I always thought that since viruses are written to attack Windows systems, a Unix based system is safe, inherently. 
Poll: has anyone ever gotten a Virus while using Ubuntu? Not running Crossover or Parallels, with Windows running, or with Windows files installed, but on a pure Linux system, what does the virus attack? 
I may be showing my Noob naivite here, but that's ok. If I am wrong, I'd rather find out in here than on my PC. 
Chappy

---

### Post by merlinus on 2007-05-16
I routinely need to send word documents, that I have received from various sources for editing, to various organizations for publication.  Whilst I am not concerned with viruses under linux, I am trying to be considerate to the recipients in case any of these was infected prior to my receiving it.

So.... chalk up one good reason for using an a-v program.

-merlin

---

### Post by Chappy7777 on 2007-05-16
Yes,
And fwiw I applaud your efforts on the behalf of others. If only more people on the net had the good of others in mind, and not the desire to cause people, especially people like my 90 yr old father, my in-laws, etc. who get really upset when their PCs go south. Not that any of us appreciate the malice intended by the creators of malware in all it's forms. 
Thnx for the explaination. And chalk one up for the "good guys". Proud to be of aquaintance Merlin.
God bless you, Chappy

---

