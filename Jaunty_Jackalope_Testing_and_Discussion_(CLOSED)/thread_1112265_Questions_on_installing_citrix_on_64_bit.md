---
title: "Questions on installing citrix on 64 bit"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cykotiktek on 2009-03-31
Has anyone had any luck with this yet?  I have a 32 bit test box that i installed 10.6 in the usual old way just unpack it cd to it ./setupwfc and go through the prompts.  But on my 64 bit test box i get this error 

/home/ghansen/en.linuxx86/./linuxx86/hinst: 236: /home/ghansen/en.linuxx86/./linuxx86/echo_cmd: not found
/home/ghansen/en.linuxx86/./linuxx86/hinst: 237: /home/ghansen/en.linuxx86/./linuxx86/echo_cmd: not found
/home/ghansen/en.linuxx86/./linuxx86/hinst: 238: /home/ghansen/en.linuxx86/./linuxx86/echo_cmd: not found
/home/ghansen/en.linuxx86/./linuxx86/hinst: 239: /home/ghansen/en.linuxx86/./linuxx86/echo_cmd: not found
/home/ghansen/en.linuxx86/./linuxx86/hinst: 4011: /home/ghansen/en.linuxx86/./linuxx86/echo_cmd: not found
/home/ghansen/en.linuxx86/./linuxx86/hinst: 4043: /home/ghansen/en.linuxx86/./linuxx86/echo_cmd: not found
/home/ghansen/en.linuxx86/./linuxx86/hinst: 4043: /home/ghansen/en.linuxx86/./linuxx86/echo_cmd: not found
/home/ghansen/en.linuxx86/./linuxx86/hinst: 4043: /home/ghansen/en.linuxx86/./linuxx86/echo_cmd: not found
/home/ghansen/en.linuxx86/./linuxx86/hinst: 4043: /home/ghansen/en.linuxx86/./linuxx86/echo_cmd: not found

like i said it's just a test box that i would like to get working on citrix so any help would be great.

---

### Post by cykotiktek on 2009-03-31
WOOHOO I got it do this to install citrix on 64 bit Jaunty

I grabbed citrix 10.6 instead of 11.0 because from what i have read it's easier.  I installed the 32 bit library's and now i have working citrix

Start out by installing ia32-libs

sudo apt-get install ia32-libs

extract enlinuxx86.tar.gz into your home director

cd enlinuxx86 

sudo ./setupwfc and follow the prompts

---

