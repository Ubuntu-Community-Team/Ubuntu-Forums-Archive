---
title: "installing citrix"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by firemansphen on 2008-05-16
I know this is going to be a simple question to answer for you linux gurus.  So here it is.

To install the Client for Unix run the setupwfc script and
follow the on-screen prompts.

I get into the terminal, to the su root and get into superuser mode so i can install into other folders other than home.

I get to the folder which holds this.. but I have no clue how to get it going lol.  It keeps saying bash doesn't know that command.  I am trying to install Citrix for work so i can login and use some programs.

If you need more info I will be checking in tomorrow.  Thanks.

Sphen

---

### Post by gabrie on 2008-05-16
> **firemansphen said:**
> I know this is going to be a simple question to answer for you linux gurus.  So here it is.

To install the Client for Unix run the setupwfc script and
follow the on-screen prompts.

I get into the terminal, to the su root and get into superuser mode so i can install into other folders other than home.

I get to the folder which holds this.. but I have no clue how to get it going lol.  It keeps saying bash doesn't know that command.  I am trying to install Citrix for work so i can login and use some programs.

If you need more info I will be checking in tomorrow.  Thanks.

Sphen

Hmmm not sure what goes wrong, but normally you would do like this:

cd /home/user/download/citrix   (folder where you downloaded the stuff and where setupwfc is)
su ./setupwfc    (so not going into superuser mode, but just su and then the command. Do notice the ./ before setupwfc)

Now accept all the defaults and install the citrix client. 

Gabrie

---

### Post by firemansphen on 2008-05-16
Thanks so much thats what i need  the " ./ " made it work!!

---

### Post by gabrie on 2008-05-17
> **firemansphen said:**
> Thanks so much thats what i need  the " ./ " made it work!!

Glad to be of help

---

### Post by Peter Freeman on 2008-05-27
Hi Gabrie,

I'm trying to install Citrix and I get it unpacked okay.  I'm following the instructions at:[https://help.ubuntu.com/community/CitrixICAClientHowTo?highlight=(Citrix](https://help.ubuntu.com/community/CitrixICAClientHowTo?highlight=(Citrix))

I have Hardy (8.04) and when I run the sudo ./setupwfc command, I get:

/home/peter/temp/./linuxx86/hinst: 236: /home/peter/temp/./linuxx86/echo_cmd: not found
/home/peter/temp/./linuxx86/hinst: 237: /home/peter/temp/./linuxx86/echo_cmd: not found
/home/peter/temp/./linuxx86/hinst: 238: /home/peter/temp/./linuxx86/echo_cmd: not found
/home/peter/temp/./linuxx86/hinst: 239: /home/peter/temp/./linuxx86/echo_cmd: not found
/home/peter/temp/./linuxx86/hinst: 4011: /home/peter/temp/./linuxx86/echo_cmd: not found
/home/peter/temp/./linuxx86/hinst: 4043: /home/peter/temp/./linuxx86/echo_cmd: not found
/home/peter/temp/./linuxx86/hinst: 4043: /home/peter/temp/./linuxx86/echo_cmd: not found
/home/peter/temp/./linuxx86/hinst: 4043: /home/peter/temp/./linuxx86/echo_cmd: not found
/home/peter/temp/./linuxx86/hinst: 4043: /home/peter/temp/./linuxx86/echo_cmd: not found

Then it just hangs up.  Any clues?

Thanks,

Peter

---

### Post by gabrie on 2008-05-27
Hi
Very sorry, but I have no clue why this is not working for you. When I ran setup, I immediately got a setup wizzard (text based).

Gabrie

---

### Post by Peter Freeman on 2008-05-29
My guess is that it is something in the script that needs a component that I have not installed.  Does anyone else have any ideas?

---

### Post by StooJ on 2010-05-13
Little late, but ran across the same problem so thought I should point out the solution for future generations.

Try this:

[http://ubuntuforums.org/showthread.php?t=450347](http://ubuntuforums.org/showthread.php?t=450347)

---

