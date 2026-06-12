---
title: "waiting for other software managers to quit"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by tehno 2 on 2010-04-07
I can not download any new programs and whenever I start to install any, it stays still forever with a statement "waiting for other software managers to quit" while there is nothing else is running.:(

---

### Post by wojox on 2010-04-07
Maybe there is something running in the background. Have you tried to reboot and install?

---

### Post by tehno 2 on 2010-04-07
> **wojox said:**
> Maybe there is something running in the background. Have you tried to reboot and install?
Thanks for your response.
this issue happens right after reboot before starting any programs. what do you mean by reboot and install. are you suggesting removing ubuntu and re-installing it??

---

### Post by wojox on 2010-04-07
No, I meant reboot and try installing something. Just to be sure what does this return from the terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by tehno 2 on 2010-04-07
I just did, excuted the your command, it starting downloading and the end gave this:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

I did that and the upgrade was completed. at the end, it showed this screen, and nothing else happens. when I try to close the window, it says:

there is still a process running on this terminal, closing the terminal will kill it (cancel) or (close terminal) 
no matter how long I wait, it keeps doing the same. 
I think, my ubuntu is corrupted and needs to be removed.
Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474;                                                                           &#8593; 
 &#9474;                                                                           &#9618; 
 &#9474; 7.  DISCLAIMER OF WARRANTY.  UNLESS SPECIFIED IN THIS AGREEMENT, ALL      &#9618; 
 &#9474;     EXPRESS OR IMPLIED CONDITIONS, REPRESENTATIONS AND WARRANTIES,        &#9618; 
 &#9474;     INCLUDING ANY IMPLIED WARRANTY OF MERCHANTABILITY, FITNESS FOR A      &#9618; 
 &#9474;     PARTICULAR PURPOSE OR NON-INFRINGEMENT ARE DISCLAIMED, EXCEPT TO      &#9618; 
 &#9474;     THE EXTENT THAT THESE DISCLAIMERS ARE HELD TO BE LEGALLY INVALID.     &#9618; 
 &#9474;                                                                           &#9646; 
 &#9474;                                                                           &#9618; 
 &#9474; 8.  LIMITATION OF LIABILITY.  IN NO EVENT WILL SUN OR ITS LICENSORS BE    &#9618; 
 &#9474;     LIABLE FOR ANY INDIRECT, INCIDENTAL, SPECIAL, CONSEQUENTIAL OR        &#9618; 
 &#9474;     PUNITIVE DAMAGES IN CONNECTION WITH OR ARISING OUT OF THIS            &#9618; 
 &#9474;     AGREEMENT (INCLUDING LOSS OF PROFITS, USE, DATA, OR OTHER ECONOMIC    &#9618; 
 &#9474;     ADVANTAGE), NO MATTER WHAT THEORY OF LIABILITY, EVEN IF SUN HAS       &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by wojox on 2010-04-08
That is the license for Java. If you want Java installed Press the <Tab> button to highlight the <OK> to accept. I would accept it if you surf the net a lot. You're bound to run into some sooner or later ( Java that is ).

---

### Post by PanTh3R on 2011-02-06
Hi sorry to use this old thread but im having the exact same problem as this person did but i already exited out of the java installation because i didnt know how to press ok on it(new to ubuntu) and now i dont know how to fix the problem all other things like 'sudo dpkg --configure -a' and 'sudo apt-get clean' dont work please help![URL="http://www.art.ubuntuforums.org/showthread.php?t=1449413"]
[/URL]

---

