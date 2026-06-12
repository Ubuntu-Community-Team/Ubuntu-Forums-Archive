---
title: "Finding a teamspeak .deb or howto"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by Matthewrd on 2006-06-10
I'm having trouble installing a teamspeak server for my guild. im wondering if anyone has experience with this, or if they know of a place i can get either a install howto or a teamspeak 2 deb. I hope this is in the correct forum as i am new to the ubuntu forums. Thank you for reading this and Thank you even more if you can post a reply to help me.
Thank you kindly,
     Matt

---

### Post by yager on 2006-06-10
I just installed this as a test including the client and had no issues.  What exactly is the challenge that you face?

---

### Post by Matthewrd on 2006-06-13
The problem i have is when i install it the way i think it should be according to the  howto i found on line and when i run the start script it doesn't work. So i know it is installed improperly i may have some dependencies issues but as of now i cant get it to work, just by the nature of my question and the answer I'm giving you now you might get that I'm rather new to Linux. I've dabbled in ubuntu Linux for about a year so i know my way around fairly well but I'm not yet able to install many programs unless its a deb, or off a ubuntu/debain repository so if there is any info from the ground up you can point me to or tell me anyone i would greatly appreciate it thanks for your fast replay sorry for taking long to get back to you.
Thank You
Matthew

---

### Post by Matthewrd on 2006-06-14
Im glad you didnt run into any problems then once i find out how i should be able to install and run it nicely :) thank you for trying to test it also 
Thank you,
Matthew

---

### Post by yager on 2006-06-14
Sorry for the not getting back sooner.  Was scanning through my old posts and checked back in on this one.

Here is what I did step by step.  See if this gets you going to be at least able to  log in as the superadmin and admin.

First download the Linux file from [www.goteamspeak.com](www.goteamspeak.com) for the server.
In my case, I downloaded the file to my Desktop.  You can download this to any location you desire but my direction will be specific to the Desktop.
[http://www.goteamspeak.com/index.php?page=downloads&id=4a](http://www.goteamspeak.com/index.php?page=downloads&id=4a)

Now uncompress the file.
You will now have a folder on your Desktop named tss_rc2

Open Applications>Accessories>terminal and change to this directory. Next execute the script to start and then stop teamspeak.
```
cd Desktop/tss_rc2
./teamspeak2-server_startscript start
./teamspeak2-server_startscript stop
```

You need to start and stop to get the passwords to the server to start with.
Now to get the passwords, type the following.
```
gedit server.log

```

Write down the passwords for the superadmin and administrator users.  You will need those at the next steps.

Restart TeamSpeak.
```
./teamspeak2-server_startscript start
```

Now open up your browser and go to the following address.
[http://localhost:14534/](http://localhost:14534/)

You are now presented with the login screen.  Choose the superadmin login link before logging in [http://localhost:14534/slogin.html](http://localhost:14534/slogin.html).  Enter the user: superadmin and the password you wrote down earlier.  You should now be in and able to make any changes you want to the server.  If you change the password, WRITE IT DOWN.  I made no changes here as it appears to be fine with the normal setup.  Now log out.

Now click on the user login link and enter the user admin and the password that you entered earlier for the admin account [http://localhost:14534/login.html](http://localhost:14534/login.html).  This is where you can set up all of your friends with user accounts and passwords if required.  If you change your admin password, write the new one down or things will be complicated if you forget this.

If you are behind a router, do not forget to set up UDP forwarding on port 8767 to your computer.  Otherwise your friends will need to be inside your firewall to access the system.

Now to actually log in and use your server, you need to download the client.  I used the same process of downloading to the Desktop, uncompressing the file and then had a folder called ts2_client_rc2_2032 on your Desktop.

Open this folder and then click on setup.sh.  This runs the installer.  Take note of where it wants to put the application.  You will need to go to that folder later in the process.  In my case, it made a folder directly off of my home folder called Teamspeak2RC2.

Browse to the folder where you installed the TeamSpeak client and then click on TeamSpeak.  I was not able to execute from the terminal so save time and just use the GUI.

To connect to your server, Click on Connection>Connect inside the TeamSpeak Client window.  This opens the connections window where you can save all of the connections you plan on using.
Enter a Label for your server and the server address.  This address is: localhost:8767
Now give yourself a nickname that will be displayed when you are logged in.
Next enter the user as admin and your password.  If you did not change your admin password, enter the same password you wrote down earlier.  This connection will be saved for later so once you get it set up, it will not need any change unless you reconfigure your server.

You are now in.

For your friends to log in, give them your IP address for your connection outside of your router if you have one, typically in the format xxx.xxx.xxx.xxx:xxxx.  If you set the router to forward port 8767, they should be able to log in.  If you have no router, they will get connected directly.  I have not tested this portion yet as I only have the one computer.

Give this a shot and let me know how far you got.  I will try to help.  If this gets over my head, I will let you know to bail out and seek "professional" help.

---

### Post by SSamiK on 2006-06-27
Nice one yager! One question...how can i make the teamspeak server start automatic after a reboot? it's....eeeeerh...hard work(?) starting it manually each time.

---

