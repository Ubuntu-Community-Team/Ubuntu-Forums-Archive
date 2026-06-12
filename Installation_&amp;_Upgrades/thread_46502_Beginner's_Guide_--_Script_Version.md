---
title: "Beginner's Guide -- Script Version"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by Mais on 2005-07-05
I've started outlining a Python-based script that will allow fresh installs to complete any of the tasks outlined in the Ubuntu Beginner's Guide. 

One of the best things about Ubuntu is it's easy access to new users and those new to Linux as well. However, if we want to really draw in a crowd of non-power-users, more still has to be done. 

Lately there have been a couple Bash and Python scripts to help set up the basics, but nothing to do it all. I understand that going through the actions listed on the beginner's page is a great learning tool, but people that are used to Windows or OSX want a computer that's automated enough that they can get to the important stuff without spending a lot of time.

So on to my outline. First of all, it needs to have an intuitive way of selecting what to setup/change and what not to. The easiest way to do this would be a GUI interface with lots of checkboxes that are categorized just as they are on the guide. A simple explanation of each would be nice as well.

In order to easily manage the large number of things that can be done, I believe that making it class-oriented would be the most effecient. A class would contain information such as the following:
```

CAT: 5 #category (in this case Add-On applications)

ID: 13 #id in category (multimedia codecs)

ARCH: i386 #what architectures this install supports. (in this case: AMD64 and PowerPC are not supported)

Requirements: 3.1, 3.2 #requires CAT.ID (in this case: backup repositries and add the extras)

Name: Multimedia Codecs #name shown to user

Description: Multimedia codecs allowing you to play many different video formats 
including Windows native formats. Requires: Extra Repositories #short description to the user and what other selections they must also make.

Warnings: Some codecs subject to patent/copyright issues. #any issues with installing the package the user should know about

Commands: [sudo apt-get install gstreamer0.8-plugins, sudo apt-get install gstreamer0.8-lame, ...] #the commands that the script will take to install them

``` 

Any suggestions are very welcome! Also, I am incapable of designing a GUI interface, I've never done that before and I haven't found a suitable tutorial yet. So, if anyone would like to do that, let me know. I'd also like some help in setting up classes based on what can be found in the guide. If you want to help with that, by all means let me know!! If someone else a bit more familiar with Linux and/or Python would like to take control of this project, let me know as well, and I'll help you out to the best of my ability.

---

