---
title: "Teamspeak,how can i install it"
date: 2015-12-11
forum: MINT
---

### Post by shane4 on 2015-12-11
Hi,

Does anyone know an easy way to install TeamSpeak in Linux Mint?

I downloaded teamspeak for linux client,and run the executable and it works..however,As soon as i minimize teamspeak client it simply disappears and disconnects the user.

I would like to install Teamspeak,so that it creates a proper shortcut icon on the desktop,and that i can make it launch automatically when i log in to my desktop.

appreciate any help. :)

---

### Post by QDR06VV9 on 2015-12-11
This is how I always install it..
[http://community.linuxmint.com/tutorial/view/2138](http://community.linuxmint.com/tutorial/view/2138)

(Shortcut or Launcher)Here is a simple shell script that will do it. If you aren't familiar with shell scripts, I'd google it. But I will try to explain.
You will open a text editor like kwrite or gedit, and put the code in, replace YOURUSERHERE with your username. Also edit the location as it reflects where you have the client folder:
```
#!/bin/sh
cd /home/YOURUSERHERE/TeamSpeak3-Client-linux_x86/
./ts3client_runscript.sh
```
When you save it, you need to make sure to call it something like TameSpeak3 or TeamSpeak3.sh... either will do.
Now you need to give it permission to run, so go to you console(Terminal) and go to the directory where you put the file and type this:
```
chmod 755 TeamSpeak3
```


If you put the .sh at the end, put that in that line as well. now when you double click the shellscript, it should bring up TS3 without the console/terminal.


Post Back if you need to.
Regards

---

### Post by shane4 on 2015-12-11
Hi,

Thank you for replying,

Okay i done the first step,creating the shell script and replaced my name in where it says "YOURNAME"...However i dont understand how to give it permission to run with the "[COLOR=#000000][FONT=Ubuntu Mono]chmod 755 TeamSpeak3"..i have put the created file in "Home"myname folder.

sorry im a noob at linux,Why they cant just put Teamspeak in the software centre is beyond me..[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2015-12-11
Hi shane4 try this
```
cd [COLOR=#000000][FONT=Ubuntu Mono]chmod 755 TeamSpeak3[/FONT][/COLOR]
```
If it is in your home directory that should work..

---

### Post by shane4 on 2015-12-11
Thanks for replying.

Its in my home directory,yet i just get this in terminal when i enter the text you provided above.

"No such file or directory"

---

### Post by QDR06VV9 on 2015-12-11
Tell me the name you gave it exactly like it is..IE:TeamSpeak3 or TeamSpeak3.sh 
<Snip>

---

### Post by shane4 on 2015-12-11
TeamSpeak3.sh  :)

---

### Post by QDR06VV9 on 2015-12-11
@shane4
Disregard with what we were doing and lets go a little easier method for the Luancher shortcut


Just go on your Desktop then Rightclick > Create a new launcher here...
Name it like you want, TeamSpeak 3 for example. Then on the command line just use the 'Browse' button to indicate the path of the 'ts3client_runscript.sh' that we have in your home /TeamSpeak3-Client-linux_amd64. file and point it to "ts3client_runscript.sh"
I have taken a screenshot of mine to show how mine looks yours will vary names..
That should be good to go now...If you have it correctly installed(TeamSpeak)
[IMG]http://i.imgur.com/lh82zyj.png[/IMG]

Oh Forgot to mention you can add a icon like i have in the same picture shown above by going to the site below..
[http://www.iconarchive.com/show/simply-styled-icons-by-dakirby309/TeamSpeak-icon.html](http://www.iconarchive.com/show/simply-styled-icons-by-dakirby309/TeamSpeak-icon.html)
Cheers

---

### Post by shane4 on 2015-12-11
Thank you so much for your help,its greatly appreciated.

Im just about to get ready for work,So il give this a try tommorow when i get back and post back if it worked.

thanks again.

---

### Post by shane4 on 2015-12-13
Sorry for the delay in replying,

Okay,i done what you said..however the "Launcher properties box" looks different on my system.

> 
[LIST]
[*]Name - Teamspeak
[*]Command - browsed & selected the TS download 64bit in my downloads.
[*]Comment - left this blank
[/LIST]

I get no option for "type"..only the three boxes above show,and "Cancel" & "OK"

But even filling out the details like you said in the box ,the OK remains grayed out..so it doesn't work :(

Seriously,why have they not added Teamspeak to Software center,makes life much easier for linux noobs.

---

### Post by QDR06VV9 on 2015-12-14
> **shane4 said:**
> Sorry for the delay in replying,

Okay,i done what you said..however the "Launcher properties box" looks different on my system.


I get no option for "type"..only the three boxes above show,and "Cancel" & "OK"

But even filling out the details like you said in the box ,the OK remains grayed out..so it doesn't work :(

Seriously,why have they not added Teamspeak to Software center,makes life much easier for linux noobs.

@shane4 I think you are making this harder than it really is.. (Sorry)I am not trying to sound Harsh here 
You should have a TeamSpeak3 Folder in your Home Directory.
I need to see if that Folder exist's, and if it dose Go inside of the folder(TeamSpeak3) and find the file called **'ts3client_runscript.sh'** and then right click on it and select <Properties> Then a Window will open, On the top you now see Tabs go to the <Permissions Tab> and down towards the bottom you will see a **"Execute"** and off to right of that Tick the box that reads **Allow executing file as program.**
Now that is also the file that your shortcut should be pointed to, and not the one in your downloads.
And it should now launch your TeamSpeak from the shortcut.
Kind Regards

---

