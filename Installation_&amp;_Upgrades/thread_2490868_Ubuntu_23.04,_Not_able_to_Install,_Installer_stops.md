---
title: "Ubuntu 23.04, Not able to Install, Installer stops post asking for login credentials"
date: 2023-09-19
forum: Installation &amp; Upgrades
---

### Post by kumarmohit1985 on 2023-09-19
I recently came across an issue with Ubuntu 23.04, 

When I try to install the same, post login credentials page the installer disappears, and nothing happens. 

Rebooted and tried multiple times same issue persists. 

For making the issue clearer please refer to the video as I am also having the same issue. - [Ubuntu 23.04 - So Broken It Wouldn't Install On My Systerm!!! - YouTube]("https://www.youtube.com/watch?v=B11PaUN6sGs&ab_channel=NovaspiritTech")

BTW, I tried installing Ubuntu 22.04 on a dual boot machine and it does get installed without any issues.

Please do help as i am on 22.04 and want to use Ubuntu 23.04.

TIA

---

### Post by yancek on 2023-09-19
Are you aware that 22.04 will be supported until April, 2027 while 23.04 will only be supported until January next year?  Is there some specific software available on 23 that is not available on 22?  

 > When I try to install the same, post login credentials page the installer disappears, and nothing happens. 
 

I don't understand that comment.  What log in credentials?  A live/install USB/DVD image doesn't have any login credentails required, at least no Ubuntu I've seen.  You should boot the installer and get to a page with the option to Try or Install.  I haven't used 23.04 so I don't know if that has changed?

---

### Post by kumarmohit1985 on 2023-09-19
Login credential means when the installer asks for username name, computer name, password and other details. Post this screen the installer disappears. 

And yes, I am aware about the support that 22.04 will get but then I thought 23.04 is better than 22.04 in terms of overall functionality. 

23.04 looks a bit polished in terms of design and the way it looks on every aspect of the OS. Though I am comfortable with 22.04 do you think 23.04 is any good over.

Can you tell me if i can use upgrade terminal commands for upgrading from 22.04 to 23.04

TIA

---

### Post by Rubi1200 on 2023-09-19
Are you seeing any error messages or the installer just disappears as you mentioned?

I would reboot the liveUSB and this time choose Safe Graphics mode so we can see whether or not to exclude that as the issue.

Also please post your specs. such as graphic card, RAM etc.

---

### Post by MAFoElffen on 2023-09-19
This happened to me while I was doing QA Testing when it was DEV, before the release... Sometimes it would time out and the screen lock would come up. Sometimes that would not work, and we filed a bug on that when it was still alpha. 

The default user is set to "user", which you should not have to enter. The password is blank, so you just have to hit the <Enter> key.

The work-around I came up for that was before installing, first go to "Try"... Then go to settings and set the Display Timeout to "Never".

Next month is when 23.10 releases. 24.04 LTS releases in 7 months. For an interim release it is imperative to keep updating the rolling release to the next or you will be orphaned. Expect all interim releases as rolling release in a snap shot of time and are not considered as STABLE, like the LTS release are, Recommended that when 24.04 gets released, that you change the apt update prompt setting to "lts"...

---

