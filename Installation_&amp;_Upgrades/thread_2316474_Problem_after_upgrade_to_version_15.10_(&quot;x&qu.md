---
title: "Problem after upgrade to version 15.10 (&quot;x&quot;-shaped cursor; no real access to GUI!!)"
date: 2016-03-08
forum: Installation &amp; Upgrades
---

### Post by Aliot_Tubu on 2016-03-08
Hey guys,
sorry, I am a complete noob and I havent got Ubuntu for very long time now, and already I ran into a problem. I believe I had the version 13.10. Today ubuntu asked whether Id like to update to the newest version and I decided to do it. I dont think the installation worked, since there popped up a couple of windows saying this or that didnt install properly (Ive sent for each a crash report). The installation nevertheless continued. After about 40 minutes the screen went black and nothing more happend, even though it stated earlier that Ubuntu would restart after the installation. I waited, but nothing happend. The screen was still black and I couldnt use the keyboard at all - so I turned my laptop off. 

When I restarted I was asked the following: 
first: to login. second: to enter my password. then a third line came up and since I didnt know what to do, I googled a bit around (knowing basically nothing about commands) and decided to go with the command: startx

I was really relieved that I got back to my desktop (with my old wallpaper/picture) and all my desktop files. But what was missing, was the sidebar and the panel at the top which consisted of the time, date, an e-mail button (to access thunderbird), etc. And even weirder: the curser turned into a black "X". Fortunately I can open the Terminal. 

I googled a bit more to solve the problem and found the following on this forum: 

>
 [B]
NOTE : THE FOLLOWING COMMAND WILL TERMINATE YOUR ACTIVE SESSION[/B]

  Enter the following commands:- Ctrl+Alt+F1 login there by user name and password 

  try sudo service lightdm restart

  If lightdm fails to get back at normal :-
  then Enter:- sudo apt-get update
  sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
     <



Before I try something I dont understand I wanted to ask you guys. 
Can anyone help me how to get it back to normal (recovery) or to make the new update work? Thank you in advance.

---

### Post by Aliot_Tubu on 2016-03-15
no one who could help out? please

---

### Post by v3.xx on 2016-03-15
Hi Aliot_Tubu

Try this in terminal
```
sudo dpkg –configure -a && sudo apt-get -f install
```

---

