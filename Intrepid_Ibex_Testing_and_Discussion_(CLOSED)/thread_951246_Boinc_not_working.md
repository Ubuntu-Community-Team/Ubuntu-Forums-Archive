---
title: "Boinc not working?"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sam Lars on 2008-10-17
After I upgraded to Intrepid, I think, Boinc is no longer uploading my work.  It keeps saying:

upload temporarily failed, HTTP error

Sending scheduler request: Requested by user.  Requesting 259200 seconds of work, reporting 1 completed tasks
Project communication failed: attempting access to reference site
Internet access OK - project servers may be temporarily down.
Scheduler request failed: Peer certificate cannot be authenticated with known CA certificates


This has gone on for at least a week or so.  I'm pretty sure this is due to my Boinc, because my other computers are checking in fine with Hardy.
I tried an aptitude reinstall with no success.
I tried an unattach from the project and a reattach with no success.

---

### Post by Peter09 on 2008-10-18
Yes, thats what is happening to me, is there any resolution to this?

---

### Post by Sam Lars on 2008-10-20
I opened a bug for it [here]("https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/286584").

---

### Post by Kevbert on 2008-10-20
Have you tried a re-install via the command line with
```
sudo apt-get install boinc-client boinc-manager
```
What projects are you using ? I don't believe Predictor@Home is sending out work units and lhcathome is rarely sending out work units due to LHC being repaired. Seti, Rosetta and Malariacontrol seem fine for me (but I'm still using Hardy).

---

### Post by Peter09 on 2008-10-20
I can get new work but cannot upload completed units. This occurred after I upgraded, until then all was ok.

---

### Post by Sam Lars on 2008-10-20
> **Kevbert said:**
> Have you tried a re-install via the command line with
```
sudo apt-get install boinc-client boinc-manager
```
What projects are you using ? 
Yes, I did an aptitude reinstall to no effect.
I'm using World Community Grid, and my other computers are getting and reporting work just fine with Hardy.

---

### Post by Kevbert on 2008-10-21
I believe the problem is discussed [[COLOR="Red"]here[/COLOR]]("http://www.worldcommunitygrid.org/forums/wcg/viewthread?thread=15682#121477"). The seems to be a number of posts regarding Intrepid on their Forum.

---

### Post by Sam Lars on 2008-10-21
Thanks for that link.
Ubuntu doesn't have any data_dir in the cc_config.xml
I also tried putting the ca-bundle.crt from a downloaded package into /etc/boinc-client, but that didn't work.
I used the deb from Get deb to update to 6.2.14, and it still has the certificate error.

---

### Post by autocrosser on 2008-10-21
I do testing work for SETI & BOINC---I just download the app--chmod 777 it after I put it in my /home & use/run it from my home directory. That way, if I update/reinstall, I keep all my information. I could give anyone that wants it a "blow-by-blow" install instructional--that bypasses the problems you have been having.

---

### Post by Sam Lars on 2008-10-22
I heard about doing it like this somewhere, and I've tried it myself, but is there a way to have the boinc service start automatically from your downloaded location?

---

### Post by Kevbert on 2008-10-22
> **autocrosser said:**
> I do testing work for SETI & BOINC---I just download the app--chmod 777 it after I put it in my /home & use/run it from my home directory. That way, if I update/reinstall, I keep all my information. I could give anyone that wants it a "blow-by-blow" install instructional--that bypasses the problems you have been having.

That would be very useful. Could you put it also on the World Community Grid Forum as well (if it's not already there ? Thanks.
A separate question as you're someone in the know. Are there any plans for Boinc screensavers for Ubuntu ? I've asked the question on the Rosetta forum and had no reply.

---

### Post by ronacc on 2008-10-22
+1 on seti screensaver in ubuntu , I had one under suse a couple of years back and liked that as my SS .

---

### Post by autocrosser on 2008-10-22
I'll put it together tonight & get it posted--as far as "auto-start"--if you are not using a testing version--6.2.15 is the latest stable--you put /home/"your_user"/BOINC/run_client  in your gnome startup session & it will start as soon as you log-in.

I'm on my way to work, but I'll write a tut as I have time--clean it up & get it to you guys asap...

I just started World computing grid, so I'll look into their forums this evening also....

As far as the screensavers--no plans that I know of--I'll ask & see....

---

### Post by Sam Lars on 2008-10-22
I finally dug through and found a solution.
I copied the ca-bundle.crt from a download of BOINC to /var/lib/boinc-client, and WCG went to work.
I'm not sure if this will hold after a reboot yet.

---

### Post by ronacc on 2008-10-22
when I open boinc-manager and select seti@home show graphics is greyed out, how do I get this to work ?

---

### Post by autocrosser on 2008-10-22
ronacc my friend--if you use my method--you will have it:)

The trick is to use the most current stable version of BOINC.

See my next post:popcorn:

---

### Post by autocrosser on 2008-10-22
As I promised--here is the way I do it & the reasons also :)


Installing BOINC to your /home folder.

I have found that doing a global install of BOINC is not the most effective way to use it. If you are to loose your system thru a reinstall or other problem, you loose BOINC also. I have used a separate /home (in a different partition) for several years so I can do testing work without data loss--this includes my BOINC install. This also allows me to update BOINC when I feel that it is time to do so.

1. GOTO the main download page for BOINC--I use the BOINC main download page ( [http://boinc.berkeley.edu/download.php](http://boinc.berkeley.edu/download.php) ) & put the script you get in your /home directory. (not your Desktop)

2. Open a terminal & input:  chmod 777 /home/"your_home"/"name of the script"  & then <enter>  This will make the script executable. Next, just put:  /home/"your_home"/"name of the script" & again hit <enter>  PLEASE make sure you DO NOT use sudo at any time during this--you want to be the MAIN owner of the data. This will install BOINC to your /home directory.

The reason you put the script in your /home instead of your Desktop?  The script makes two "helper" scripts - run_client & run_manager. They use the current location of the script as a "starting point"--as long as you know that it is easy to "fix" a script that points to the wrong place--such as moving the location of the main BOINC folder. 

A typical script looks like:  cd "/home/dean/BOINC" && exec ./boincmgr $@   

As you can see it points to the location & then starts the Manager.

3. Next your need to create a startup in your gnome session (I have not used KDE, but I would think that there is a similar way for it)...

Open up your gnome sessions preferences & ADD a new startup program--put in /home/"your_home"/BOINC/run_manager & save it. I know that all of you are thinking that you need to put "run_client" in, but the manager will startup the client as part of its duties--this holds true for the current stable version of BOINC--the older versions & the new testing version need "run_client" there because the client is not auto-started. 

You can also just start the current stable manager as a program without any problem--I include a menu item in my Menu Accessories section--there as a couple of good icons in the BOINC folder for that purpose. This allows you to start/stop the daemon & application AT THE SAME TIME.

The created BOINC folder has it's own ca-bundle.crt, so you don't rely on the system you are running & ALL data is saved to the BOINC folder EXCEPT for the BOINC Manager status file--that is in your dot files in your home directory as .BOINC Manager

As you can see, BOINC becomes "portable"--if you need to make a new /home, just move the BOINC folder--rename things in the scripts if you need to & move .BOINC Manager to the new /home directory & then restart BOINC---Job done.

Updating your BOINC install is even easier--just download the new BOINC--chmod 777 it (making sure it is in your /home directory) & then run the script. It will update the required elements & keep your data intact.

---

### Post by ronacc on 2008-10-22
Thanks dean I'll try that tomorrow AM when I fire up my intrepid box again , I've got boinc running under hardy on my "main sys" I'll try your method for intrepid although I havent got a seperate /home there . This close to release It might be better to wait, I'm intending to do a complete wipe and reinstall after release .

---

### Post by autocrosser on 2008-10-22
The beauty of doing it this way is that it will not matter which OS your are using--it's all run from your /home. I HIGHLY recommend a separate partition for your /home--it has saved me many times!!! I use different partitions for all three of my installs--Have a Hardy & currently two Ibex--one will be Jaunty very soon...... :)

---

### Post by ronacc on 2008-10-23
I normaly do run a seperate /home , thats one of the reasons I want to do a reinstall after release . I had several disasters with the early alpha's that took out my /home and I just got lazy and started doing default installs for the test phase . To be honest the early days were looking so dire for me that I was begining to wonder if it would ever become a useable system for me ( edgy never did ) so I was expecting to dump it and move to jaunty on day one . Intrepid is on my "test" box anyway that NEVER gets used for anything productive , over the years I've learned the hard way not to let alphas anywhere near my "main" system .

---

### Post by ronacc on 2008-10-23
I installed boinc per your instructions in my /home in intrepid , show graphics is no longer greyed out but does nothing when clicked ( with seti selected) when I start the manager from term  I get connect: connection refused and then connect: operation now in progress  .  I have xhost +local:  in my session startup .

---

### Post by cometta on 2008-10-23
just copy the cert into /var/lib/boinc-clinet folder and it will work. it work for me. and it will work for you too..  

donate your cpu idle cycles for science .. save the world !

---

### Post by autocrosser on 2008-10-23
I don't use xhost--are you using the newest stable seti? What version of BOINC did you D/L?

If it's the 5 series--move to 6.2.XX

I'm at work right now--can look in more depth this evening......


> **ronacc said:**
> I installed boinc per your instructions in my /home in intrepid , show graphics is no longer greyed out but does nothing when clicked ( with seti selected) when I start the manager from term I get connect: connection refused and then connect: operation now in progress . I have xhost +local: in my session startup .

---

### Post by ronacc on 2008-10-23
the version is boinc_6.2.15_x86_64-pc-linux-gnu.sh direct from the boinc website. I added the xhost +local: because I had seen that in another thread but with or without no difference . I'll delete that from my session startup .

---

### Post by autocrosser on 2008-10-23
Yes--6.2.15 is the current stable version--Not sure why you are not getting graphics--I just checked & I get graphics in AstroPulse--no SETI units running right now....

---

### Post by ronacc on 2008-10-23
I don't see astropulse in the projects selection list or I would signup for that too m boxes actualy sit idle most of the time so they might as well do someting useful .
edit :  the seti@home on my intrepid just uploaded its first completed work unit no problem .

---

### Post by ronacc on 2008-10-23
ok I read a bit more about astropulse , as I understand it the work units for that aslo come from seti so you might get either type I guess I just have to wait until I get one of those to see I the graphics work there .

---

### Post by autocrosser on 2008-10-24
Astropulse will determine if your computer "meets" it's standards--my quad will turn out a A/P unit in about 40hours, so it is a bit time intensive :)--I can crunch four at a time---Q9550 3.0......

You could look at World Community Grid--nice graphics there--I also run SETI@Home beta--the new 6.03 seti app runs very fast....I know for sure that it has nice graphics--that is the new Multi-Beam project.

---

### Post by ShirishAg75 on 2008-10-24
hi all, 
 look at the [lpbug] 246205 [/lpbug] and see the workaround discussed therein. The workaround suggested there works for me on 6.2.12 without an issue :)

 First time was able to use the in-house (Ubuntu) boinc-client on the box. Otherwise each time had to get the latest from boinc.berkley.edu and don't really like that experience.

---

