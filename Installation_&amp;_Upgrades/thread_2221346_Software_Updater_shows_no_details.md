---
title: "Software Updater shows no details"
date: 2014-05-01
forum: Installation &amp; Upgrades
---

### Post by RainerEL on 2014-05-01
After switching from 12.04 to 14.04 I got intermeadiate problems with the Software Updater. The checking for update starts and then I got "Failed to download repository information Please check your Internet connection". No hints whats happen (I gues wrong or stopped repositories), no chance to click to details or any eroor messages. Under 12.04 it was possible to select details and see whats going wrong.

It is nice for unexpiernce user to see no error infos, but it doesn't help.

What can I do to see whats going wrong?

---

### Post by Old_Grey_Wolf on 2014-05-01
When the GUI method doesn't work nor provide information, I switch to the CLI and use the commands ```
sudo apt-get update && sudo apt-get upgrade
```

I use the output of the commands for troubleshooting.

---

### Post by RainerEL on 2014-05-01
Thanks Old-Grey-Wolf,

this helps to circumvent the problem. But still is the question why is the GUI method changed to being bad?

---

### Post by Old_Grey_Wolf on 2014-05-01
I don't use 14.04. I use 12.04 that is 2 years old. This is not a new problem. Depending on the error, it happens in 12.04 as well.

---

### Post by RainerEL on 2014-05-01
Under 12.04 I have been seeing the updating activity and the errors on the GUI. Under 14.04 I don't see this in the GUI. The upadting is reduced to a smal window and no chance for any activity displaying.

That is my question: Why is the activity displaying removed under 14.04?

---

### Post by Old_Grey_Wolf on 2014-05-01
Are you using Ubuntu, Xubuntu, or Lubuntu?

I downloaded Ubuntu 14.04, installed it, and now running 63 MBs of updates while watching the Details being displayed in the Software Updater.

---

### Post by Old_Grey_Wolf on 2014-05-01
If you are still having problems with the Software Updater, post the output of the commands I gave you to the forum between code tags. Go Advanced and click the # button. A screenshot of the GUI with no Details menu shown would be helpful for anyone trying to help you.

---

### Post by RainerEL on 2014-05-02
Hi Old-Grey-Wolf,

the problem is not at the time of intalling. Theare see all activity. The problem is during the "apt-get update" part of the Software Updater GUI.

Here are my output of apt-get update, please note the errors are clear for me. The GUI should show this errors and the activity to me, like under 12.04.
```
rainer@BN591:~$ sudo apt-get update
[sudo] password for rainer: 
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://archive.canonical.com trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://de.archive.ubuntu.com trusty InRelease                              
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://de.archive.ubuntu.com trusty-updates InRelease                      
Hit http://security.ubuntu.com trusty-security Release                         
Hit http://archive.canonical.com trusty Release                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://de.archive.ubuntu.com trusty-backports InRelease                    
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://de.archive.ubuntu.com trusty Release.gpg                            
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://de.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://de.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://de.archive.ubuntu.com trusty Release                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://de.archive.ubuntu.com trusty-updates Release                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://de.archive.ubuntu.com trusty-backports Release                      
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://de.archive.ubuntu.com trusty/main amd64 Packages                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://de.archive.ubuntu.com trusty/restricted amd64 Packages              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://de.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://de.archive.ubuntu.com trusty/multiverse amd64 Packages              
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://de.archive.ubuntu.com trusty/main i386 Packages                     
Ign http://archive.canonical.com trusty/partner Translation-en                 
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://de.archive.ubuntu.com trusty/restricted i386 Packages               
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty Release.gpg                      
Ign http://extras.ubuntu.com trusty/main Translation-en              
Hit http://de.archive.ubuntu.com trusty/universe i386 Packages       
Ign http://ppa.launchpad.net trusty Release.gpg                      
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://de.archive.ubuntu.com trusty/multiverse i386 Packages     
Hit http://ppa.launchpad.net trusty Release.gpg                      
Hit http://ppa.launchpad.net trusty Release.gpg
Hit http://de.archive.ubuntu.com trusty/main Translation-en
Hit http://ppa.launchpad.net trusty Release.gpg
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://ppa.launchpad.net trusty Release.gpg
Ign http://ppa.launchpad.net trusty Release.gpg
Hit http://de.archive.ubuntu.com trusty/multiverse Translation-en    
Hit http://ppa.launchpad.net trusty Release.gpg                      
Hit http://de.archive.ubuntu.com trusty/restricted Translation-en
Hit http://ppa.launchpad.net trusty Release    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://de.archive.ubuntu.com trusty/universe Translation-en                
Hit http://ppa.launchpad.net trusty Release                          
Hit http://de.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://ppa.launchpad.net trusty Release                          
Hit http://de.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Ign http://ppa.launchpad.net trusty Release                          
Hit http://de.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://ppa.launchpad.net trusty Release                          
Hit http://de.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://ppa.launchpad.net trusty Release                          
Hit http://de.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://ppa.launchpad.net trusty Release                          
Hit http://de.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Hit http://de.archive.ubuntu.com trusty-updates/universe i386 Packages
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US
Hit http://ppa.launchpad.net trusty Release    
Hit http://de.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Ign http://ppa.launchpad.net trusty Release                          
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Hit http://ppa.launchpad.net trusty Release                          
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US      
Hit http://ppa.launchpad.net trusty/main Sources                     
Hit http://de.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://de.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://ppa.launchpad.net trusty/main Sources
Hit http://de.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://de.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://de.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://de.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://de.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://de.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://ppa.launchpad.net trusty/main Sources
Hit http://de.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://de.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://de.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://de.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://ppa.launchpad.net trusty/main Sources
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://de.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://de.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://de.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://de.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://ppa.launchpad.net trusty/main Sources
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main Sources
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main Sources
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main Sources
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Ign http://de.archive.ubuntu.com trusty/main Translation-en_US
Ign http://de.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://de.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://de.archive.ubuntu.com trusty/universe Translation-en_US
Ign http://de.archive.ubuntu.com trusty-updates/main Translation-en_US
Ign http://de.archive.ubuntu.com trusty-updates/multiverse Translation-en_US
Ign http://de.archive.ubuntu.com trusty-updates/restricted Translation-en_US
Ign http://de.archive.ubuntu.com trusty-updates/universe Translation-en_US
Ign http://de.archive.ubuntu.com trusty-backports/main Translation-en_US
Ign http://de.archive.ubuntu.com trusty-backports/multiverse Translation-en_US
Ign http://de.archive.ubuntu.com trusty-backports/restricted Translation-en_US
Ign http://de.archive.ubuntu.com trusty-backports/universe Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/geod/ppa-geod/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/geod/ppa-geod/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/opencpn/opencpn/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/opencpn/opencpn/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
rainer@BN591:~$ 

```

And here are the screnshots of the Software Updater GUI:

[ATTACH=CONFIG]252731[/ATTACH][ATTACH=CONFIG]252732[/ATTACH]

The question is: why I don't see the activity and errors in the GUI which occurs in the command line command ??

---

### Post by Old_Grey_Wolf on 2014-05-02
I didn't say during the install, I said during the update afterward. I done 2 updates and both showed details. I tried entering one of the invalid ppa's from the error message you posted into sources.list, and still got details including the Could not fetch...404 Not Found error. I have been unable to reproduce the problem on Ubuntu 14.04. Maybe someone else can answer your question.

---

### Post by RainerEL on 2014-05-06
Hi Old_Grey_Wolf,

many thanks.

This must be a customition problem. Some parameters deep in the customition. Would be nice i anybody now which one.

Thanks again Rainer

---

