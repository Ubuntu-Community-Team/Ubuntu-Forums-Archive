---
title: "boinc"
date: 2009-12-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-12-13
autocrosser got me into this boinc-alpha stuff.  It is his fault.

I have been using Stoned Lizard as my production daytime OS.  Somehow I got it royally screwed (it is the one I have been most conservative with upgrading).

With the way boinc was installed (his fault - his fault - nah nah), I was able to just copy paste the bugger over here to Lounge Lizard and take right off where I was in stoned Lizard.

This is great.  Thanks autocrosser.

---

### Post by ronacc on 2009-12-13
link to his install instructions please . I would run boinc on my test box if I had a way to continue after a reinstall  ( I do that alot during testing :P) .

---

### Post by Kevbert on 2009-12-13
Best way to install BOINC is with
```
sudo apt-get install boinc-client boinc-manager
```
Then add a new project via 'Tools','Attach to project' via boinc menus.
Works fine for me in Ubuntu 10.04.

---

### Post by ronacc on 2009-12-13
I did it that way during jaunty but wasn't able to migrate my "partials" to a fresh install .

---

### Post by autocrosser on 2009-12-13
I'll post my testing Alpha install information---And Kevbert--that's a OK way to install the current stable BOINC---but it has none of the advantages for localized install...

This way BOINC is installed to your /home & as such, will only be damaged if you nuke your home---The global install that installs vis repo installs in a way that CAN NOT be easily removed & replaced during a system install.......Here is how.

Installing BOINC to your /home folder.

I have found that doing a global install of BOINC is not the most effective way to use it. If you are to loose your system thru a reinstall or other problem, you loose BOINC also. I have used a separate /home (in a different partition) for several years so I can do testing work without data loss--this includes my BOINC install. This also allows me to update BOINC when I feel that it is time to do so.

1. GOTO the main download page for BOINC--I use the BOINC main download page ( [http://boinc.berkeley.edu/download.php](http://boinc.berkeley.edu/download.php) ) & put the script you get in your /home directory. (not your Desktop)

2. Open a terminal & input: chmod 777 /home/"your_home"/"name of the script"  & then <enter>  This will make the script executable. Next, just put: /home/"your_home"/"name of the script" & again hit <enter>  PLEASE make sure you DO NOT use sudo at any time during this--you want to be the MAIN owner of the data. This will install BOINC to your /home directory.

The reason you put the script in your /home instead of your Desktop?  The script makes two "helper" scripts - run_client & run_manager. They use the current location of the script as a "starting point"--as long as you know that it is easy to "fix" a script that points to the wrong place--such as moving the location of the main BOINC folder. 

A typical script looks like:  cd "/home/dean/BOINC" && exec ./boincmgr $@   

As you can see it points to the location & then starts the Manager.

3. Next your need to create a startup in your gnome session (I have not used KDE, but I would think that there is a similar way for it)...

Open up your gnome sessions preferences & ADD a new startup program--put in /home/"your_home"/BOINC/run_manager & save it. I know that all of you are thinking that you need to put "run_client" in, but the manager will startup the client as part of its duties--this holds true for the current stable version of BOINC--the older versions & the new testing version need "run_client" there because the client is not auto-started. 

You can also just start the current stable manager as a program without any problem--I include a menu item in my Menu Accessories section--there as a couple of good icons in the BOINC folder for that purpose. This allows you to start/stop the daemon & application AT THE SAME TIME.

The created BOINC folder has it's own ca-bundle.crt, so you don't rely on the system you are running & ALL data is saved to the BOINC folder EXCEPT for the BOINC Manager status file--that is in your dot files in your home directory as .BOINC Manager

As you can see, BOINC becomes "portable"--if you need to make a new /home, just move the BOINC folder--rename things in the scripts if you need to & move .BOINC Manager to the new /home directory & then restart BOINC---Job done.

Updating your BOINC install is even easier--just download the new BOINC--chmod 777 it (making sure it is in your /home directory) & then run the script. It will update the required elements & keep your data intact.


Please contact me if you want to test BLEEDING edge BOINC--I can get people in touch with the project manager & the "way" to get the current testing code.

---

### Post by ronacc on 2009-12-13
thanks

---

### Post by autocrosser on 2009-12-13
Happy Testing!!!!

---

### Post by ranch hand on 2009-12-14
I need to get my chosen daytime production OS working again and transfer this info back to it.  Then I will go for the testing boinc again.

I haven't checked in 9.04 but the ...17 is in the Lounge Lizard repo.

---

### Post by autocrosser on 2009-12-14
You need to update to .24--it is the most in need of testing---most likely will be the next "stable" release.

---

### Post by ranch hand on 2009-12-14
I actually have it downloaded, I just need to get the current one back to Stoned Lizard from Lounge Lizard (where I am now), then I will upgrade to ...24.

Is there anything I need to do differently to get my WU and so forth transfered from one version to another or will it just install on the existing files and leave the content there?

I still haven't gotten the OS to work so I may just do it here and then transfer it over whan I get it working.  Just remove the old one and put ...24 in its place.  Everything, of coarse, has been finished from what I transfered anyway.

---

### Post by autocrosser on 2009-12-14
Just replace the base files as I outline---all the data files are not touched & the new manager will complete a upgrade (or downgrade--it works either way) without any outside help.

---

### Post by ranch hand on 2009-12-14
OK, re-read the instructions, looks like a painless update.  I will do in on here and just get rid of the old one on Stoned Lizard and when I get it working just transfer the ...24 from here to there.

Thanks.

---

### Post by ranch hand on 2009-12-14
Boinc 2.10.24 up and running on Lounge Lizard.  Looking good.

I was chicken and saved my "projects" folder just in case.  I can delete it now as everything updated flawlessly.

---

### Post by autocrosser on 2009-12-14
Yes---Dave & the guys have it down pretty well...I've been working with SETI & then later BOINC for over 10 years now & the crew has always been super!!!

(I started crunching Oct 1999-----)

---

### Post by ranch hand on 2009-12-14
That is a little while.

I have heard about this type of crunching for some time but have never had a reliable enough connection.  I really like the ability to do this now.

---

### Post by ranch hand on 2009-12-19
I am having less trouble with this version than I had with ...17.  I run the cpus full bore with the only limitation being that if I need more boinc will give it up.  It waits until I REALLY need it.

The ...17 froze the whole system if I was using more than 3 windows of FF about once a day.  I have only had that with ..24 once so far.

The only problem is HFCC graphics.  I am with World Community Grid and that is Help Fight Childhood Cancer.  I can pull up any of the others fine.  HFCC graphics is a good replacement for the old Ctrl + Backspace.  It restarts X.

I do not usually look at that crap but we are supposed to be testing.

Now all I need to do is get TB straight on my new main OS I will send soething to the "list on it" just found it today and ought to be able to do mail tomorrow.  Just ran out of time tonight.

---

### Post by ranch hand on 2010-01-03
OK another weird question from a guy with too many OS'.

If I pop over to one of my other 10.04 installs and decide to stay for a while, what happens to boinc if I just pull it up, on nautilus, and start it from the OS it is installed on?

I have never put it on the menu or have it set to auto start.  When I boot up the normal install I just open nautilus>boinc and start the "manager".  I can do this from another OS, through nautilus, too.  I tried it and chickened out after a few seconds as I do not know what this is going to do if it uploads, reports or downloads another WU from a different OS even though it is being run from the files on the "proper" OS.

Yes I do know that I am crazy.

---

### Post by autocrosser on 2010-01-03
Won't work that way---needs the .BOINC Manager file in the root of the user you are using & it will have a hard time sync'ing with all the /BOINC files---unless you make simlinks to the file (s)--never tried it, but it could be interesting..............

---

### Post by ranch hand on 2010-01-03
I was just screwing around while trying to get a good burn on an ISO for 8.04..3 on my Lxde Lizard and pulled up the Lounge Lizard files and right clicked on the "manager" and hit the option to open and it did and then I thought "well lets see if it will run" (suspended before leaving Lounge).  It did and then I thought "Oh great, probably not a good idea" and suspended it again.

Thought I would throw it out there and see what folks thought.  Nautilus is great, that was done without being root, but it sure will let you get into more trouble than you think if you are like a monkey in a banana plantation.

---

