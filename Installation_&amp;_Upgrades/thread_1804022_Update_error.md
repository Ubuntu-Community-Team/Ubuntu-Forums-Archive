---
title: "Update error"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by cantonas11 on 2011-07-14
I've noticed recently that an error icon keeps appearing on my panel. When I mouse over it, it reads "The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by clicking on this icon and then selecting 'Check for updates' and check if some of the listed repositories fail.".
I used the Update Manager to check for security patches. When I do so, there are a few sources that failed. How do I correct this error? I have already run "sudo apt-get update" but this doesn't solve the issue.
Oh. I'm running Ubuntu 10.04 LTS by the way.

---

### Post by matt_symes on 2011-07-14
Hi

Open up konsole and copy and paste

```
sudo apt-get update
```

Enter your password. It will not be echoed to the screen. 

Copy and paste the results back here. It will tell us which sources are failing without using screen shots.

Kind regards

---

### Post by pict4169 on 2011-07-14
[COLOR=Red]**remove the s/w and reinstall that**[/COLOR]

---

### Post by matt_symes on 2011-07-14
Hi

> **pict4169 said:**
> [COLOR=Red]**remove the s/w and reinstall that**[/COLOR]

That's overkill. This can be fixed.

Kind regards

---

### Post by cantonas11 on 2011-07-19
The result from running "sudo apt-get update" is:

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_SG   
Ign [http://ppa.launchpad.net/docky-core/ppa/ubuntu/](http://ppa.launchpad.net/docky-core/ppa/ubuntu/) lucid/main Translation-en_SG
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_SG
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/docky-core/stable/ubuntu/](http://ppa.launchpad.net/docky-core/stable/ubuntu/) lucid/main Translation-en_SG
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_SG
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_SG
Ign [http://ppa.launchpad.net/moonlight-team/pinta/ubuntu/](http://ppa.launchpad.net/moonlight-team/pinta/ubuntu/) lucid/main Translation-en_SG
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [44.7kB]
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) lucid/main Translation-en_SG
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) lucid/main Translation-en_SG
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Ign [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/) lucid/main Translation-en_SG
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                       
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]         
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                  
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid Release.gpg                               
Ign [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_SG            
Ign [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_SG      
Ign [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_SG        
Ign [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_SG      
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid-updates Release.gpg                       
Ign [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_SG    
Ign [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_SG
Ign [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_SG
Ign [http://sg.archive.ubuntu.com/ubuntu/](http://sg.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_SG
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid Release                                   
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid-updates Release                           
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/main Packages                             
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/restricted Packages                       
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/main Sources                              
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/restricted Sources                        
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/universe Packages                         
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/universe Sources                          
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/multiverse Packages                       
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid/multiverse Sources                        
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid-updates/main Packages                     
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid-updates/restricted Packages               
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid-updates/main Sources          
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid-updates/restricted Sources    
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid-updates/universe Packages     
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid-updates/universe Sources      
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid-updates/multiverse Packages   
Hit [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) lucid-updates/multiverse Sources    
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                   
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [14.0kB]                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages                
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [1,506B]                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources                 
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [752B]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                  
  416  Requested Range Not Satisfiable 20003
Fetched 61.8kB in 17s (3,441B/s)                                                 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3AD52A40B98E84D3
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/lucid/main/source/Sources.gz](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/lucid/main/source/Sources.gz)  416  Requested Range Not Satisfiable 20003

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cantonas11 on 2011-07-19
I tried "autoclean" and then "update" again. Doesn't solve the issue.

---

### Post by smurphy_it on 2011-07-19
You could try this persons script to automatically find and grab any of your missing keys.

[http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/](http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/)

---

### Post by matt_symes on 2011-07-19
Hi

> W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 3AD52A40B98E84D3
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/")  lucid Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: Failed to fetch [http://ppa.launchpad.net/pidgin-deve...rce/Sources.gz]("http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/lucid/main/source/Sources.gz")  416  Requested Range Not Satisfiable 20003


This is your problem. You are missing some keys.

Have a look at this page.

[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

Kind regards

---

### Post by Old_Grey_Wolf on 2011-07-19
If you are like me and don't want to download someone's script and reading every command it to to know if it is safe to run, you can copy and paste these 6 commands in a terminal and execute them one at a time in order to get the missing keys:

```
gpg --keyserver keyserver.ubuntu.com --recv 3AD52A40B98E84D3

gpg --export --armor 3AD52A40B98E84D3 | sudo apt-key add -

gpg --keyserver keyserver.ubuntu.com --recv 9BDB3D89CE49EC21

gpg --export --armor 9BDB3D89CE49EC21 | sudo apt-key add -

gpg --keyserver keyserver.ubuntu.com --recv A6DCF7707EBC211F

gpg --export --armor A6DCF7707EBC211F | sudo apt-key add -
```

What the commands do:

1) gpg --keyserver <keyserver name> --recv <key identifier>
It retrieves the GPG key from the key server.

2) gpg --export --armor <key identifier> | sudo apt-key add -
It exports the key in ASCII to be used as input to the piped "|" command that adds the key to apt.
The piped command uses sudo; therefore, you will need to enter your password before the command is executed.

After you have executed those 6 commands, when you run the command 'sudo apt-get update' you should not get these errors. If you do get errors, copy and post the errors.

---

### Post by cantonas11 on 2011-07-20
Wolf, after following your steps... I still have 2 broken keys.

[I]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG 9BDB3D89CE49EC21 Launchpad PPA for Mozilla Team
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures were invalid: BADSIG A6DCF7707EBC211F Launchpad PPA for Ubuntu Mozilla Security Team
W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/lucid/main/source/Sources.gz](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/lucid/main/source/Sources.gz)  416  Requested Range Not Satisfiable 20003

E: Some index files failed to download, they have been ignored, or old ones used instead.[/I] 

Is there also a way to fix the keys without opening a high port on my host firewall?

---

### Post by Old_Grey_Wolf on 2011-07-20
Enter these commands one at a time in the terminal```

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
exit
```

---

### Post by brolin_1911a1 on 2011-07-24
I'm getting the same error saying that my 11.04 updates are now 31 days old. My error messages say that it's an inability to reach certain Natty Narwal repositories.
 -----------------
W:Failed to fetch [http://canonical.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://canonical.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://canonical.ubuntu.com/ubuntu/dists/natty/partner/binary-amd64/Packages](http://canonical.ubuntu.com/ubuntu/dists/natty/partner/binary-amd64/Packages)  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://canonical.ubuntu.com/ubuntu/dists/natty/partner/i18n/Translation-en](http://canonical.ubuntu.com/ubuntu/dists/natty/partner/i18n/Translation-en)  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.
  -------------------

Any suggestions?

---

### Post by Old_Grey_Wolf on 2011-07-24
> **brolin_1911a1 said:**
> I'm getting the same error saying that my 11.04 updates are now 31 days old. My error messages say that it's an inability to reach certain Natty Narwal repositories.
 -----------------
W:Failed to fetch [http://canonical.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://canonical.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://canonical.ubuntu.com/ubuntu/dists/natty/partner/binary-amd64/Packages](http://canonical.ubuntu.com/ubuntu/dists/natty/partner/binary-amd64/Packages)  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://canonical.ubuntu.com/ubuntu/dists/natty/partner/i18n/Translation-en](http://canonical.ubuntu.com/ubuntu/dists/natty/partner/i18n/Translation-en)  Something wicked happened resolving 'canonical.ubuntu.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.
  -------------------

Any suggestions?

Use gedit /etc/apt/sources.list to edit the lines in the file that have [http://cononical.ubutu.com/](http://cononical.ubutu.com/).... to [http://archive.ubuntu.com/](http://archive.ubuntu.com/)....

---

### Post by nick12inferno on 2011-07-24
[SIZE=4]i also got the same error on my panel :(...and this is what its showing me ..


[FONT=monospace]W: Failed to fetch [http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/nikount//ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/nikount//ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/nikount//ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/nikount//ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/FONT][/SIZE]

---

### Post by Old_Grey_Wolf on 2011-07-24
> **nick12inferno said:**
> [SIZE=4]i also got the same error on my panel :(...and this is what its showing me ..


[FONT=monospace]W: Failed to fetch [http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/nikount//ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/nikount//ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/nikount//ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/nikount//ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/FONT][/SIZE]

I would Google nikount ppa and Google baudm ppa; then, follow their instructions to change your sources settings in synaptic to point to the PPA's new location. They have moved their packages to another URL.

---

### Post by Old_Grey_Wolf on 2011-07-24
More information. nikount seems to be a theme; therefore, I don't think there would be a problem with commenting "# " out that entry in your /etc/apt/sources.list file using gedit. I don't know what baudm is.

---

### Post by nick12inferno on 2011-07-25
[SIZE=3]owh...

can you plz guide me ...am new to ubuntu.,,,,its the 1st time i have came across this thing........
[/SIZE]

---

### Post by Old_Grey_Wolf on 2011-07-25
I won't have time for a few days to research you PPA repository problems. I suggest that you start a new thread for your problem. People usually don't look at old threads with 17 responses that have been hijacked twice.

---

### Post by Old_Grey_Wolf on 2011-07-29
> **nick12inferno said:**
> [SIZE=3]owh...

can you plz guide me ...am new to ubuntu.,,,,its the 1st time i have came across this thing........
[/SIZE]

I see that you did not follow my advice and start a new thread. Just in case you are still waiting for an answer...

Use the command ```
gedit /etc/apt/sources.list
``` to open an editor. Remove the lines in the file that have:
"http://ppa.launchpad.net/nikount//ubuntu/dists/natty/main/source/Sources", 
"http://ppa.launchpad.net/nikount//ubuntu/dists/natty/main/binary-i386/Packages", 
"http://ppa.launchpad.net/baudm/ppa/ubuntu/dists/natty/main/source/Sources", and 
"http://ppa.launchpad.net/nikount//ubuntu/dists/natty/main/binary-i386/Packages"
 in them. Then save the file.

Then enter these commands one at a time in a terminal ```
sudo add-apt-repository ppa:nikount/orta-desktop
sudo add-apt-repository ppa:baudm
sudo apt-get update
sudo apt-get install orta-theme
sudo apt-get install gyachi
```

---

### Post by cantonas11 on 2011-08-07
I get new errors when running apt-get update now.
[I]
W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/lucid/main/source/Sources.bz2](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/lucid/main/source/Sources.bz2)  Hash Sum mismatch

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.bz2](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

[/I]@Wolf... how do I fix the "Hash Sum mismatch" error?

---

### Post by Cammigirl on 2011-08-07
I'm having the same problem and when I follow the instructions below,

> **matt_symes said:**
> Hi

Open up konsole and copy and paste

```
sudo apt-get update
```Enter your password. It will not be echoed to the screen. 

Copy and paste the results back here. It will tell us which sources are failing without using screen shots.

Kind regards

I get this:
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/bisigh/ppa/ubuntu/](http://ppa.launchpad.net/bisigh/ppa/ubuntu/) lucid/main Translation-en_US   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) lucid/main Translation-en_US   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages             
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
  404  Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
W: Failed to fetch [http://ppa.launchpad.net/bisigh/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/bisigh/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Please advise.

Also, upon booting, I keep getting a "recovery mode" boot in ubuntu.  I have a dual-boot system.

---

### Post by brolin_1911a1 on 2011-08-07
I don't have a clue regarding the recovery mode boot problem but you might find an answer to the missing repository problem in the discussion here... [https://answers.launchpad.net/linuxdcpp/+question/157582](https://answers.launchpad.net/linuxdcpp/+question/157582) .

i recently upgraded to Nasty Narwhal from Maverick Meerkat and kept getting a similar error with regard to the mozilla repositories.  I finally noticed that I'd misspelled the name as "mozzila."  The repositories can be edited using Synaptic Package manager.  Choose the Settings>Repositories menu selection, then scroll down the list of repositories to the one you want to change, then hit the [edit] button to make any needed changes.

---

