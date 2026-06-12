---
title: "WUBI INstaller First time installation username password error"
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by apocalypsereturns on 2012-02-16
I have installed Wubi  and then UBUNTU using this ,

During entering UBUNTU it asks for a user name and password,
The one which i gave in WUBI are not working 


Also i have tried to enter into ROOT shell but have not been able to as there is not option to enter ( UBUNTU has not been installed yet )  

THe options which i have are 
normal 
Safe graphics 
Demo ACPi (something  i am not sure about this one )


PLease help as i have reinstalled this WUBI several times and every time it ask for the user name and password

---

### Post by bcbc on 2012-02-16
You shouldn't be prompted for a password before it's installed. Maybe it doesn't like something about the username/password you entered. Are you using any special characters or just the standard stuff? Can you hit Ctrl+Alt+F1 when you get the problem and zip the logs:
```
sudo sh /host/ubuntu/install/custom-installation/hooks/failure-command.sh
```
or if that gives any error:
```
sudo zip -r /host/ubuntu/installation-logs.zip /var/log
```

Then you can attach C:\ubuntu\installation-logs.zip to your next post.

---

### Post by apocalypsereturns on 2012-02-19
hi thanks for the reply ..
 

I am using just my name as my password so there should not be any problem.

The password being asked maybe is the one provided during the first phase of WUBI



I will take the log using the steps you just mentioned . Ihope that works 
as what i could see in the list of codes was a very limited option.

Maybe sudo was one of them..


I will get back to you in some time .


Thanks a lot though..

---

### Post by apocalypsereturns on 2012-02-19
> **bcbc said:**
> You shouldn't be prompted for a password before it's installed. Maybe it doesn't like something about the username/password you entered. Are you using any special characters or just the standard stuff? Can you hit Ctrl+Alt+F1 when you get the problem and zip the logs:
```
sudo sh /host/ubuntu/install/custom-installation/hooks/failure-command.sh
```
or if that gives any error:
```
sudo zip -r /host/ubuntu/installation-logs.zip /var/log
```

Then you can attach C:\ubuntu\installation-logs.zip to your next post.
hi i tried pressing Ctrl+alt+f1   ,
i got a black screen which was allowing to me enter stuff ,

but i dont thik they were command as  after entering any command i was not getting any response  .

I am getting the error in the GUI so i presses CTRL+ATL+F7 maybe to go back to the GUI and then restarted the computer .

---

### Post by bcbc on 2012-02-19
What you're describing doesn't make sense to me. You shouldn't be prompted for your username and password. When installing Wubi, after rebooting, it either loads up straight into Ubuntu (preinstalled install method) or does the 2nd phase installation which is unattended (no user input) and then it reboots. When you are prompted to enter your password it should be the graphical login and the username is presented (doesn't have to be entered). Wubi uses your Windows username as the 'Description' for the account and this is what you'll see, although the actual user name is what you entered when running wubi.exe.

So let's start with the basics. Please post your wubi log file (from the %TEMP% directory and it's called wubi-nn.nn-revnnn.log e.g. for 11.10 it'll be wubi-11.10-rev24x.log where x can be 1 or 5).

---

### Post by apocalypsereturns on 2012-02-20
> **bcbc said:**
> What you're describing doesn't make sense to me. You shouldn't be prompted for your username and password. When installing Wubi, after rebooting, it either loads up straight into Ubuntu (preinstalled install method) or does the 2nd phase installation which is unattended (no user input) and then it reboots. When you are prompted to enter your password it should be the graphical login and the username is presented (doesn't have to be entered). Wubi uses your Windows username as the 'Description' for the account and this is what you'll see, although the actual user name is what you entered when running wubi.exe.

So let's start with the basics. Please post your wubi log file (from the %TEMP% directory and it's called wubi-nn.nn-revnnn.log e.g. for 11.10 it'll be wubi-11.10-rev24x.log where x can be 1 or 5).
OK right now i am not at my home PC so i wont be able to give you the log file in the temp dir .

But let me List out the Steps that i followed 

1) Download Wubi
2) Download the 32bit ISO (As the 64Bit was not working , it was giving some CD/DVD not found     error )

you can append my previous post after these steps .


I will get back to you with teh log file in %temp% as soon as i can.
3) PLaced the 32bit Ubuntu 11.10 ISO in C drive so that it is the first ISO found by Wubi 
    ( it took some time going through the log so find out why it was not picking up the 32 Bit , But      finally i got it working )
4) Wubi  asked For a user name and password  ( It wouldn't allow me to go ahead without one, Also the username had to begin with a small Cap )
5) Wubi installed the Files in the drive i had specified and then rebooted the computer for the second phase.


Phase 2 

6) the Computer booted and went directly to ubuntu ( I did not get the multiple bootscreen for the first time  , i believe that's the default action for the first time)

7) First thing i noticed is that i was getting a prefix error  but that did not stop the booting process so i guess that's OK.
8 ) Count down to interrupt the Operation and to select other booting options (  no recovery mode is present in the list) 

9) Boot into Ubuntu ( The purple screen with Dots flowing ) 

10) As soon as i enter the main ubuntu screen it asks for this user name and password  and it wont accept anything i throw at it .

---

### Post by bcbc on 2012-02-20
The 2nd phase of the installation is supposed to be unattended but there are some cases where you will be prompted... usually if there is a error. Wubi (in windows) is supposed to only accept valid data but there are some known issues. So you mentioned that the first letter of the username had to be lower case. In fact the whole user name should be lower case. Can you confirm that it was? otherwise that might explain this. If need be try a simple username and password to rule this out

---

### Post by apocalypsereturns on 2012-02-20
I am trying a simple password and username all are small caps , and they don't even exceed 8 letters .
I have found a log related to WUBI but that is the same log file which i  got created during the First phase no additions to the file were made during the second phase.

Is there is any way in which i could make sure that WUBI is completely un installed from my PC so that i could start a fresh INstall , as everytime i uninstall and then re install i am getting the same message.( password issue)


Thanks for trying to help me out here.

---

### Post by bcbc on 2012-02-20
> **apocalypsereturns said:**
> I am trying a simple password and username all are small caps , and they don't even exceed 8 letters .
I have found a log related to WUBI but that is the same log file which i  got created during the First phase no additions to the file were made during the second phase.

Is there is any way in which i could make sure that WUBI is completely un installed from my PC so that i could start a fresh INstall , as everytime i uninstall and then re install i am getting the same message.( password issue)


Thanks for trying to help me out here.
Everytime you install, it uninstalls the old one. Or you can go to the control panel, Add/remove programs, and find the "Ubuntu" entry and uninstall it.

But Wubi doesn't remember things between installs. How about this: next time it happens, hit Ctrl+Alt+F1 and capture the logs:
```
sudo zip  -r  /host/ubuntu/installation-logs.zip  /var/log
```

Then [create a new bug report]("https://bugs.launchpad.net/wubi/+filebug"), and attach the logfile (also the Wubi install log). 

PS the logs you capture will be on the drive you installed on e.g. C:\ubuntu\installation-logs.zip  if you installed on C:

---

### Post by apocalypsereturns on 2012-02-23
i tried what you said  but no log was createdhence am unable to post the log here.
i also went to fold you specified . there is no installation log .zip created.

The sceen which comes up after ctrl + alt + f1  wont accept any commands  it does to give any comfirmation of commands.

---

### Post by bcbc on 2012-02-23
How about that wubi log file then?

---

