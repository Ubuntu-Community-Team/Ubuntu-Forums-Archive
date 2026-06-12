---
title: "hardy 8.04 -&gt; no longer updating"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by kyleabaker on 2008-04-29
I've been using Ubuntu Hardy Heron 8.04 since Alpha 1 and have been very pleased with it. Very few problems have occurred the entire time.

The problem I'm having all of a sudden now though, is that I am no longer getting updates to any of my software!

It all started on the 24th (when 8.04 was released). On that day, I ran update-manager (as I do daily) and I could tell that the servers were swamped. It got to repo. 15 of like 42 and just stuck for a while.

After a couple days, that problem disappearred, but I've not recieved a single update/upgrade to any of my software in 5 days now! I was getting like ~50-60 updates per day a little while back.

I understand that they were pushing plenty of updates to reach the release day, but I'm thinking my update-manager is just not working anymore.

For example, I have virtual-box-ose installed and after the header update a little while back, update-manager never updated the modules for virtual-box-ose. I opened synaptic package manager and found the update sitting there, but it was never updated automatically. Manually updating it fixed virtual box for me.

A lot of the repos have "Ign" in front of them in the terminal. I never noticed this before, but I'm assuming it means ignored? Example, here are the first 5 repos from the terminal:
```
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://archive.canonical.com hardy Release.gpg                   
Ign http://archive.canonical.com hardy/partner Translation-en_US  
```

I want to start getting updates again! So basically..has anyone received an update to 8.04 in the last 5 days (not counting the upgrade that many did)?

---

### Post by bsh on 2008-04-29
same here, i am not able to update, update manager is unable to download package information files.
tried changing mirrors, not helped.

---

### Post by bsh on 2008-04-29
lol... this is strange. i use vnc to login to the box, to :1 screen, and the update manager doesn't work properly on that.
i have just went to the pc, logged in locally to :0, and it worked perfectly.
very strange.

---

### Post by Hotwheelz79 on 2008-04-29
Hi guys,

I would like 2 offer a suggestion that being ask your isp if they do\operate  a local mirror for ubunntu updates. 
If so try changing the sources.list  file to reflect this.

I know my isp does this and they are not the only ones that I know of

It's a good idea todo this since the main paths listed in file by can somtimes be down due to load on server.

Plus u might find that u will save yourself some download qouta because by getting your updates via your isp it's seen as internel traffic therefore not counted towards your qouta.

Give it a try and report back if u want.

Thanks. 

:-)

---

### Post by kyleabaker on 2008-04-29
I'm currently at school, so the whole isp thing won't work for me.

Have you been receiving updates properly over the last ~5 days?

---

### Post by spudratic on 2008-04-29
I have not gotten one single update also.This is why I stopped today.I upgraded on the day of the release and not one update.Is there a page that list all the updates that came out since the release or a way to find out what updates were released.

---

### Post by kyleabaker on 2008-04-29
@spudratic
I've wondering about an update log for some time now. That would be excellent! I'm not aware of one, but surely there is.

Anyhoo, before I get this thread off topic/hijacked I'd like to get my updates working again.

---

### Post by kyleabaker on 2008-05-01
Come on people. Is there not a guru here that can help? I came across the following thread, but nothing helped there either:
[http://ubuntuforums.org/showthread.php?t=758039](http://ubuntuforums.org/showthread.php?t=758039)

I thought the last post would work (changing source locations), but it didn't.

Here is what happens when I update in the terminal:
```

$ sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US          
Hit http://archive.canonical.com hardy Release                            
Hit http://archive.canonical.com hardy/partner Packages                  
Hit http://archive.canonical.com hardy/partner Sources
Get:1 http://archive.ubuntu.com hardy Release.gpg [191B]
Ign http://archive.ubuntu.com hardy/main Translation-en_US
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Get:2 http://archive.ubuntu.com hardy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Get:3 http://archive.ubuntu.com hardy-security Release.gpg [191B]
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US      
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US        
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US      
Hit http://archive.ubuntu.com hardy Release                                    
Hit http://archive.ubuntu.com hardy-updates Release                            
Hit http://archive.ubuntu.com hardy-security Release                           
Hit http://archive.ubuntu.com hardy/main Packages                              
Hit http://archive.ubuntu.com hardy/restricted Packages                        
Hit http://archive.ubuntu.com hardy/main Sources                               
Hit http://archive.ubuntu.com hardy/restricted Sources                         
Hit http://archive.ubuntu.com hardy/universe Packages                          
Hit http://archive.ubuntu.com hardy/universe Sources                           
Hit http://archive.ubuntu.com hardy/multiverse Packages                        
Hit http://archive.ubuntu.com hardy/multiverse Sources                         
Hit http://archive.ubuntu.com hardy-updates/main Packages                      
Hit http://archive.ubuntu.com hardy-updates/restricted Packages                
Hit http://archive.ubuntu.com hardy-updates/main Sources                       
Hit http://archive.ubuntu.com hardy-updates/restricted Sources                 
Hit http://archive.ubuntu.com hardy-updates/universe Packages                  
Hit http://archive.ubuntu.com hardy-updates/universe Sources                   
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages                
Hit http://archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://archive.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Hit http://archive.ubuntu.com hardy-security/main Sources
Hit http://archive.ubuntu.com hardy-security/restricted Sources
Hit http://archive.ubuntu.com hardy-security/universe Packages
Hit http://archive.ubuntu.com hardy-security/universe Sources
Hit http://archive.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.ubuntu.com hardy-security/multiverse Sources
Fetched 573B in 21s (27B/s)
Reading package lists... Done

```

What does, Hit mean? And Ign? How can I fix this?

---

### Post by vexorian on 2008-05-01
Hit means it hit it, IGN means it ignored it.

The reason you are not getting any updates is that there aren't updates...

There are 69 updates in the hardy proposed repo though. (Go to synaptic's repositories dialog there's some part in which you can enable backports and proposed)

---

### Post by randysparks on 2008-05-01
There's definitely a problem with the Ubuntu repo servers today. None are responding quickly. Some won't work at all. I'm using the UK server right now and it's VERY SLOWLY updating the repo lists. 

Let's hope this is a temporary fault and not something in the code of the Hardy release... :(

---

### Post by isharra on 2008-05-01
> **kyleabaker said:**
> I've been using Ubuntu Hardy Heron 8.04 since Alpha 1 and have been very pleased with it. Very few problems have occurred the entire time.

The problem I'm having all of a sudden now though, is that I am no longer getting updates to any of my software!

The point in a beta/development cycle is to push changes out as quickly as possible in order to test the software before release. So while Hardy was in development you saw frequent updates.

The point in a Long Term Stability Release is to have as few changes as possible in order to maintain stability and not have any unpleasant surprises for production systems.  So now that Hardy is official you should NOT be seeing updates unless it is for a bug fix.

Everything is working as designed, the lack of updates is not a problem.
 
The update servers not being accessible is a problem will be corrected.

Log files may depend on what program you use to update the system, but I see files /var/log/dpkg.log, /var/log/apt/term.log and /var/log/aptitude which tell me about my updates.

---

### Post by SnakeHips on 2008-05-01
isharra post: agreed +1

"There's definitely a problem with the Ubuntu repo servers today. None are responding quickly. Some won't work at all. I'm using the UK server right now and it's VERY SLOWLY updating the repo lists."

you can always try another server

menu/apps/system/software sources
click on "download from"
select "other"
click on "best server"
it'll give you the "fastest" not necessarily the closest. ;-)

---

### Post by kyleabaker on 2008-05-01
> **isharra said:**
> The point in a beta/development cycle is to push changes out as quickly as possible in order to test the software before release. So while Hardy was in development you saw frequent updates.

The point in a Long Term Stability Release is to have as few changes as possible in order to maintain stability and not have any unpleasant surprises for production systems.  So now that Hardy is official you should NOT be seeing updates unless it is for a bug fix.

Everything is working as designed, the lack of updates is not a problem.
 
The update servers not being accessible is a problem will be corrected.

Log files may depend on what program you use to update the system, but I see files /var/log/dpkg.log, /var/log/apt/term.log and /var/log/aptitude which tell me about my updates.
As I stated earlier:
> I understand that they were pushing plenty of updates to reach the release day, but I'm thinking my update-manager is just not working anymore.
Even when I was using 7.04 and 7.10 there were updates at least once a week.

---

### Post by vexorian on 2008-05-01
Hasn't it been less than a week since the release?

---

### Post by kyleabaker on 2008-05-01
Well, 1 week today.

---

### Post by isharra on 2008-05-01
> **kyleabaker said:**
> As I stated earlier:

Even when I was using 7.04 and 7.10 there were updates at least once a week.

You have missed my point.  7.04 and 7.10 were NOT Long Term Support releases. LTS releases such as Hardy 8.04 are intended to have less changes than standard releases. They have official support for longer than regular releases as well. 

Ubuntu 6.06 the last LTS release, could go a month between updates for me even though I check daily. (2 to 3 updates a month was typical.)

If you have the logwatch package installed, you'll see a list of what packages you have updated in the daily reports. I subscribe to the ubuntu security announcement list to make sure I'm up to date (although usually the update has already been installed before I see the announcement) and there are no hardy postings there either.

---

### Post by kyleabaker on 2008-05-01
@isharra
I know what you're saying now. I just like to see the process of development, so I guess I'll have to wait about a month for some work on 8.10 to start so I can join them. :D Thanks.

---

### Post by spudratic on 2008-05-01
had some thing strange this mourning.the icon was in the panel.put the cursor over it  the balloon tip came up telling me I had updates.clicked on it update manager opened did its thing no updates.One more trouble to add to list of things that don't work quite right.That being said it is solid.

---

### Post by fogcat on 2008-05-01
Odd...I cannot connect to any update servers..are they down? 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  

Log shown....

---

### Post by DRHamp on 2008-05-03
OK, this morning -- Hardy automatically detected an available update -- downloaded & installed.

I'm now comfortable that all is working as it should.

---

### Post by kyleabaker on 2008-05-03
**Thread Solved**

---

### Post by bsh on 2008-05-05
no, there's something wrong with the update manager. it just doesn't work in a vnc session for me.

---

