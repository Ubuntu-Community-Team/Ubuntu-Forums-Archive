---
title: "I just upgraded to 11.10 and can't get past the login screen."
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by OsakaWilson on 2011-10-14
It lists my username along with 'Guest session' and 'Other', but when I select it and put in my password, the screens go black for a moment, then return to the login screen as if nothing happened. 

However, if I put in the wrong password, I get the usual "Invalid Password" message. This means that it recognizes that my password is correct, but fails to take me to the desktop. 

I have no idea if this is relevant, but during upgrade, I got a screen called something like "Defconf in Ubuntu". It wanted me to put a password in twice (to create a password, maybe). It mentioned something about "Tripwire". I attempted to put in a password several times, but it failed, so selected skipping that step. It told me I could do it later. Like I say, not sure if it is relevant. 

I'm on 64 bit upgrading from 11.04 and had at least three successful pushbutton upgrades previously, it that helps.

---

### Post by garvinrick4 on 2011-10-14
Can you Hit"
ctrl/alt/F1
Log in 
password
```
sudo dpkg-reconfigure lightdm
```Does that give you both gdm and lightdm?
If so choose lightdm with arrows enter and or tab to toggle with I believe.
```
sudo stop gdm
``````
sudo start lightdm
```If needed
```
sudo /etc/init.d/lightdm restart
```###This above is just incase gdm is still present. You are getting to a log in screen so might not be problem but worth looking at since old upgraded system.

---

### Post by OsakaWilson on 2011-10-14
Thanks. I did the ctrl/alt/F1 then logged in. I did the "sudo dpkg-reconfigure lightdm" command and it gave me both the gdm and lightdm as options. I chose the lightdm. 

I tried to input the "sudo stop gdm" command, but it said "stop: Unknown instance:" The same for "sudo start lightdm"

(I went back to the login GUI and tried again with no luck.) 

I noticed that the GUI login gives me the option of <my initials>, but not <my name>, however the login after the ctrl/alt/F1 would not accept <my initials>, but did login successfully using <my name> . Of course, I tried going back to the login GUI and used <my name> to log in, but it also failed. 

I'm pretty sure that <my name> shows up in the command line and definitely I see it in the file location trees. And it allows me to login to ctrl/alt/F1, but not the GUI when I select "other" then input <my name> and password. Sorry if this is not useful info.

---

### Post by kchida on 2011-10-14
> **OsakaWilson said:**
> I have no idea if this is relevant, but during upgrade, I got a screen called something like "Defconf in Ubuntu". It wanted me to put a password in twice (to create a password, maybe). It mentioned something about "Tripwire". I attempted to put in a password several times, but it failed, so selected skipping that step. It told me I could do it later. Like I say, not sure if it is relevant. 

I'm getting the same problem, but I didn't have the "Defconf in Ubuntu" thing that you described.

---

### Post by OsakaWilson on 2011-10-14
Garvinrick4 didn't mention the "tripwire" thing, so I suspect that is irrelevant. 

Out of curiosity, is the login name on your login GUI the same as what you use normally in your system?

---

### Post by garvinrick4 on 2011-10-14
> I noticed that the GUI login gives me the option of <my initials>,  but not <my name>, however the login after the ctrl/alt/F1 would  not accept <my initials>, but did login successfully using <my  name> . Of course, I tried going back to the login GUI and used  <my name> to log in, but it also failed. 

Your login screen will give you what you said as your Name at install. (If I chose Rick Garvin at install would have made login rick and at login screen Rick Garvin)
If you can get to the tty as you say. ctrl/alt/F1 then login and password:
Try installing aptitude and see if you have both gdm and lightdm installed.
We want to use lightdm in oneiric 11.10, gdm was phased out after 11.04
```
sudo apt-get install aptitude
``````
aptitude show gdm
``````
aptitude show lightdm
```If gdm is still installed
```
sudo apt-get purge gdm
``````
sudo apt-get install --reinstall lightdm
``````
sudo start lightdm
```if needed
```
sudo /etc/init.d/lightdm restart
```##Or you can use my previous post to choose lightdm in reconfigure command.

###This above is just incase gdm is still present. You are getting to a  log in screen so might not be problem but worth looking at since old  upgraded system.

---

### Post by grim2 on 2011-10-14
Ok.  I tried all that was listed and I still have the problem.  In another thread I mentioned that I have two accounts on this machine.  The admin account is the one that gets used.  I had it set up to use Gnome rather than Unity.  It's broken.  The other account, standard user, had Unity as an interface.  It's fine.

I'm not sure if that helps.  I certainly appreciate yours.

g2

---

### Post by savvar on 2011-10-14
> **garvinrick4 said:**
> Your login screen will give you what you said as your Name at install. (If I chose Rick Garvin at install would have made login rick and at login screen Rick Garvin)
If you can get to the tty as you say. ctrl/alt/F1 then login and password:
Try installing aptitude and see if you have both gdm and lightdm installed.
We want to use lightdm in oneiric 11.10, gdm was phased out after 11.04
```
sudo apt-get install aptitude
``````
aptitude show gdm
``````
aptitude show lightdm
```If gdm is still installed
```
sudo apt-get purge gdm
``````
sudo apt-get install --reinstall lightdm
``````
sudo start lightdm
```if needed
```
sudo /etc/init.d/lightdm restart
```##Or you can use my previous post to choose lightdm in reconfigure command.

###This above is just incase gdm is still present. You are getting to a  log in screen so might not be problem but worth looking at since old  upgraded system.

tried that but still same login issue. 

another think i noticed is that on login screen shutdown/restart will not work also. dont know if thats helpful

---

### Post by uk144 on 2011-10-14
I found that the shutdown failed in the login screen too ( in addition to my password not working)

---

### Post by savvar on 2011-10-14
problem is only with my existing login. created new user with terminal and it works fine (the new user)

---

### Post by uk144 on 2011-10-14
Can you let me know how to do it in console . can you ascribe admin access to this?

---

### Post by savvar on 2011-10-14
> **uk144 said:**
> Can you let me know how to do it in console . can you ascribe admin access to this?

"adduser newuser" command will create a new general user called "newuser" on your system

---

### Post by savvar on 2011-10-14
it seems that it logins the user in when i type the passw but still brings me back to login screen.

maybe its because i was using different theme on that user?


pls can an1 help


any ways to bring default theme back with terminal?

thnx

---

### Post by zebrattt on 2011-10-14
> **savvar said:**
> problem is only with my existing login. created new user with terminal and it works fine (the new user)

 I have the same problem.   after reading your description, I tried to log in using guest,  it works.

but we still need to fix the problem.  I don't want to create a new user.

---

### Post by OsakaWilson on 2011-10-14
I tried everything that Garvinrick4 suggested and it didn't work. 

Like everyone else, my Shutdown/Restart on the login screen is also not working. 

I could login as a guest, but the point is accessing the stuff on my account and being able to make system changes.

---

### Post by 23dornot23d on 2011-10-14
Check out the login problems ...... one is marked as solvedd in my list below

you may be having the same problem ......

Failure Graphics - Lightdm
[http://ubuntuforums.org/showthread.php?t=1859133](http://ubuntuforums.org/showthread.php?t=1859133)
       Login Problem
[http://ubuntuforums.org/showthread.php?t=1859288](http://ubuntuforums.org/showthread.php?t=1859288)
[http://ubuntuforums.org/showthread.php?t=1859349](http://ubuntuforums.org/showthread.php?t=1859349)
[http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233) >>> [COLOR=Red]**SOLVED**[/COLOR][COLOR=Green]
[[COLOR=Black]http://ubuntuforums.org/showthread.php?t=1859373[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1859373")[/COLOR]

---

### Post by uk144 on 2011-10-14
> **23dornot23d said:**
> Check out the login problems ...... one is marked as solvedd in my list below

you may be having the same problem ......

Failure Graphics - Lightdm
[http://ubuntuforums.org/showthread.php?t=1859133](http://ubuntuforums.org/showthread.php?t=1859133)
       Login Problem
[http://ubuntuforums.org/showthread.php?t=1859288](http://ubuntuforums.org/showthread.php?t=1859288)
[http://ubuntuforums.org/showthread.php?t=1859349](http://ubuntuforums.org/showthread.php?t=1859349)
[http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233) >>> [COLOR=Red]**SOLVED**[/COLOR][COLOR=Green]
[[COLOR=Black]http://ubuntuforums.org/showthread.php?t=1859373[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1859373")[/COLOR]
This one worked for me

[http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233) >>> SOLVED

rm .Xauthority

thanks

---

### Post by zebrattt on 2011-10-14
> **23dornot23d said:**
> Check out the login problems ...... one is marked as solvedd in my list below

you may be having the same problem ......

Failure Graphics - Lightdm
[http://ubuntuforums.org/showthread.php?t=1859133](http://ubuntuforums.org/showthread.php?t=1859133)
       Login Problem
[http://ubuntuforums.org/showthread.php?t=1859288](http://ubuntuforums.org/showthread.php?t=1859288)
[http://ubuntuforums.org/showthread.php?t=1859349](http://ubuntuforums.org/showthread.php?t=1859349)
[http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233) >>> [COLOR=Red]**SOLVED**[/COLOR][COLOR=Green]
[[COLOR=Black]http://ubuntuforums.org/showthread.php?t=1859373[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1859373")[/COLOR]

Thank u!   my problem is fixed!

---

### Post by OsakaWilson on 2011-10-14
This is the *meat* of the thread that fixed it. I logged in fine after this.
 
> Press Ctrl+Alt+F1 when you're on login screen. Then login under your profile. The default directory will be your home directory. Then simply do:
Code:

sudo rm .Xauthority

Code:

sudo shutdown -r now

Then you should be able to login under your profile.


---

### Post by blackknight95857669 on 2011-10-14
> **OsakaWilson said:**
> This is the *meat* of the thread that fixed it. I logged in fine after this.

I've tried this 10 times.  Each time I reboot I get the same result: can't get past login.

Trying to figure what more I need to do, if there's a KDE thing I have left over that's causing the issue or some other "old" package that's getting in my way.  Every time I reboot the .Xauthority has returned and is owned by root.  I even changed the ownership and it still won't let me login to my original account.

Just this lame guest acct :-?#-o

Also, opening the Update Manager, I get the "Partial Upgrade" warning, but when I click it, it shuts down the Manager.  Guessing that's due to not being in an admin account.

---

### Post by savvar on 2011-10-14
> **uk144 said:**
> This one worked for me

[http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233) >>> SOLVED

rm .Xauthority

thanks


for me 2. now all ok thnx guys

---

### Post by suffah on 2011-10-14
I hit this issue upgrading from 11.04 to 11.10 64 bit.

My fix is different than the rest.

I realized I didn't have an .Xauthority folder in my home directory, so I tried to create one.  It said I didn't have permission.  :P

It turns out that somehow my home folder was now owned by a user "1016" instead of my user "suffah", but all the recursive files and folders were still owned by "suffah".

I used "sudo chown suffah:suffah /home/suffah" which did the trick.

---

### Post by grim2 on 2011-10-14
All.  Removing .Xauthority worked for me too.

Thanks for your help.

g2

---

### Post by dldeskins on 2011-10-15
> **23dornot23d said:**
> Check out the login problems ...... one is marked as solvedd in my list below

you may be having the same problem ......

Failure Graphics - Lightdm
[http://ubuntuforums.org/showthread.php?t=1859133](http://ubuntuforums.org/showthread.php?t=1859133)
       Login Problem
[http://ubuntuforums.org/showthread.php?t=1859288](http://ubuntuforums.org/showthread.php?t=1859288)
[http://ubuntuforums.org/showthread.php?t=1859349](http://ubuntuforums.org/showthread.php?t=1859349)
[http://ubuntuforums.org/showthread.php?t=1859233](http://ubuntuforums.org/showthread.php?t=1859233) >>> [COLOR=Red]**SOLVED**[/COLOR][COLOR=Green]
[[COLOR=Black]http://ubuntuforums.org/showthread.php?t=1859373[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1859373")[/COLOR]


the one marked "solved" worked for me also... delete the .Xauthority file and reboot.

---

### Post by edgardol on 2011-10-15
Deleting .Xauthority and rebooting didn't work for me either.
Details posted here: [http://ubuntuforums.org/showthread.php?t=1859233&page=2](http://ubuntuforums.org/showthread.php?t=1859233&page=2)

---

### Post by dbzkid on 2011-10-17
What I did was
```
Alt + F2
login
sudo apt-get purge gdm
sudo chmod 777 .Xauthority
```
That allowed me to login in using my regular profile.
Hope this helps

---

### Post by Morce on 2011-10-28
Hi. I have tested all the options available in this thread and others, so far nothing as solved the problem.
Removed the Xauthority and after reboot (several) it does not reappear again (can't delete it again) or start the session. I say it does not reappear because I have read, in other threads, that it as reappeared after reboot. 
I have the ubuntu 11.10 64b, at login I can't login with any account (mine, guest or other) but password is correct it just resets to login screen. I have access to tty.

Does anyone know how to solve this???

ps: Ubuntu works perfect as long as you don't do updates, almost every time I update, I have to come to ubuntu forums for problem solving. Someone always knows the answer and that is very helpful.

Thank you.

---

