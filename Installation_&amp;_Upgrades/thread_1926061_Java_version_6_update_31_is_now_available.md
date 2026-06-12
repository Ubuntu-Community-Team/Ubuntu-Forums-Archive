---
title: "Java version 6 update 31 is now available"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by Cavsfan on 2012-02-15
The latest version of Java - version 6 update 31 just became available today.
The [COLOR=Red]red link[/COLOR] in my signature will check what version you have installed. 
If it says you do not have version 6 update 31 installed it will provide a link to download it. Download the ".bin" file and not the ".rpm" file.
The [COLOR=Green]green link[/COLOR] will provide instructions to remove the previous version and install the new version.
It has already been updated for version 6 update 31, so it's just a matter of copying and pasting.

I just performed the update myself and it's good to go.

If you have a 32 bit machine, the instructions are on the left down a  ways, for 64 bit machines the right side has the instructions.

It says to remove the old version first and mentions the instructions for doing that are towards the bottom. 
There is a link that will put you at the removal instructions.
Then you just start from the top and copy and paste the commands and you should be good to go. :smile:

Then you may want to check out the How to in [COLOR=Blue]blue[/COLOR] in my signature. It is really good for dual booting and having a grub menu that 
never changes even when a new kernel in installed and having a custom backround picture of your choice.
But, it is not just for dual booting. You can have Ubuntu only and it will work.

---

### Post by davesmith on 2012-02-18
Hi Cavsfan

Well now i have a java problem. Firefox put out an update 10.0.2, which I installed. I also noticed that java upgraded, so I added 

<deb [http://www.duinsoft.nl/pkg](http://www.duinsoft.nl/pkg) debs all> to my sources.list again

and used theDuinsoft script "update-sun-jre" to remove sun-java6u30 and installed the new java version 6u31. Using this method has worked well in the past - but now the java website does not recognise my ugraded java installation and a number of websites that use java dont work.

Do you have any ideas as to what might have gone wrong?

PS - Just to make life really difficult, right-click copy and paste is disabled!

---

### Post by Cavsfan on 2012-02-18
> **davesmith said:**
> Hi Cavsfan

Well now i have a java problem. Firefox put out an update 10.0.2, which I installed. I also noticed that java upgraded, so I added 

<deb [http://www.duinsoft.nl/pkg](http://www.duinsoft.nl/pkg) debs all> to my sources.list again

and used theDuinsoft script "update-sun-jre" to remove sun-java6u30 and installed the new java version 6u31. Using this method has worked well in the past - but now the java website does not recognise my ugraded java installation and a number of websites that use java dont work.

Do you have any ideas as to what might have gone wrong?

PS - Just to make life really difficult, right-click copy and paste is disabled!

I don't think you want both java and update-sun-jre. 
You can use [[color=blue]_http://www.duinsoft.nl/packages.php_[/COLOR]](http://www.duinsoft.nl/packages.php) to uninstall it.
You could probably just use this command **sudo update-sun-jre -v remove**
You will probably want to remove the deb and the key listed on that site too.

Then you should be able to redo installation via my link. 
It mentions you need to open **Applications** > **Ubuntu Software Center** and query for **icedtea** and remove that if it is installed.
Also remove any previous version of java (instructions for removal are towards the bottom) you have installed before installing 6.31.
You should be able to remove it and re-install it over and over with no problems. The version of java in the Lucid repository is 6.26 I'm pretty sure.

Use Ctrl and c to copy highlighted text and Ctrl and v to paste. That works when right clicking for copy and paste doesn't.
Once you do the method mentioned in my signature, you will need to get further updates manually.
You could make bookmarks of the 2 links. I try to post a new thread when I notice the new version is out.
Let me know if you get it working.

---

### Post by davesmith on 2012-02-20
Hi
I can't get it working. I removed "update-sun-jre" and installed 6u31 as described in your link - but the java website wont recognise it. And none of my firefox java sites work.

So I have the latest firefox 10.0.2, the latest java 6u31 but something is wrong. Do you have any ideas? I spent half the weekend trying to fix it

---

### Post by Cavsfan on 2012-02-20
> **davesmith said:**
> Hi
I can't get it working. I removed "update-sun-jre" and installed 6u31 as described in your link - but the java website wont recognise it. And none of my firefox java sites work.

So I have the latest firefox 10.0.2, the latest java 6u31 but something is wrong. Do you have any ideas? I spent half the weekend trying to fix it

I'm sorry you are having such problems. I have firefox 10.0.2 and java 6.31 as well and everything works great.
When you enter ```
about:plugins
``` in the web address at the top does it say:
```
Java(TM) Plug-in 1.6.0_31

    File: libnpjp2.so
    Version: 
    The next generation Java plug-in for Mozilla browsers.
```
If it does not, I would go back through it once more slowly until you see the above.
Remove everything like it says at the bottom and then start back at the top.
If it does, I don't really know what to tell you. I have never had any problems with it. 
Even new Ubuntu users have used this method and it worked flawlessly.

If all of the above look correct and it still doesn't work, you might try posting in this thread: 
[[COLOR=blue]_Comprehensive Multimedia & Video Howto _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

Someone there most probably can help you.
Let me know what happens.

---

### Post by beaver29 on 2012-02-22
I've had similar problems installing Java under Ubuntu.  I have always had to manually tell Firefox where to find the Java plugin in the "libnpjp2.so" file.  Instructions for doing this are in these threads:

  [http://ubuntuforums.org/showthread.php?t=1905492](http://ubuntuforums.org/showthread.php?t=1905492)

  [http://ubuntuforums.org/showthread.php?t=1896122](http://ubuntuforums.org/showthread.php?t=1896122)

  [http://ubuntuforums.org/showthread.php?t=1899035](http://ubuntuforums.org/showthread.php?t=1899035)

hope this helps!

---

### Post by davesmith on 2012-02-23
Thank you both for your help.I'll try the links this weekend. I will get it to work!

---

### Post by Cavsfan on 2012-02-25
> **beaver29 said:**
> I've had similar problems installing Java under Ubuntu.  I have always had to manually tell Firefox where to find the Java plugin in the "libnpjp2.so" file.  Instructions for doing this are in these threads:

  [http://ubuntuforums.org/showthread.php?t=1905492](http://ubuntuforums.org/showthread.php?t=1905492)

  [http://ubuntuforums.org/showthread.php?t=1896122](http://ubuntuforums.org/showthread.php?t=1896122)

  [http://ubuntuforums.org/showthread.php?t=1899035](http://ubuntuforums.org/showthread.php?t=1899035)

hope this helps!


Installing the Firefox plugin starts in the _[COLOR=SeaGreen]How to Update Java[/COLOR]_ link with step 11 and continues through to the end.
Right after that is the instructions for removal, which it says to perform first.

The instructions are pretty straight forward. You just have to follow them closely.

I hope you get it sorted out.

---

### Post by davesmith on 2012-02-26
I solved the problem by doing a clean re-install of the OS. Firefox and java work well now.
Thanks for your help
Regards

---

### Post by Cavsfan on 2012-02-26
> **davesmith said:**
> I solved the problem by doing a clean re-install of the OS. Firefox and java work well now.
Thanks for your help
Regards

You are welcome. Sorry to hear it took a clean install! I have done stuff earlier in my learning days of Ubuntu 
that I had to do a clean install because I messed things up.
Glad you got it working and if you use my method in the future, it should work.
I have upgraded to the latest Java via this method at least a dozen times without any problems.
Happy Ubuntuing!!! :)

---

### Post by LEdesigns on 2012-03-31
Thank you! That's a long process, but worked great.  I've been scratching my head trying to get sun-java working so Aleks Math will work.  Now I can deploy edubuntu for a school classroom.

---

### Post by Cavsfan on 2012-04-01
> **LEdesigns said:**
> Thank you! That's a long process, but worked great.  I've been scratching my head trying to get sun-java working so Aleks Math will work.  Now I can deploy edubuntu for a school classroom.


You are very welcome! I am very glad I could help! I copy the commands to a gedit notepad file and modify that if necessary 
then past them back into the terminal. It has been working for over a year now. :)

---

### Post by Cavsfan on 2012-04-03
I noticed where version 7 is in beta so it should be coming down the pipe soon.

---

### Post by priority on 2012-04-04
hello. i am trying to install Java 6.31 but i couldnt.. pls can u tell me how to do it ?? 

your green link doesnt work for me..

---

### Post by Cavsfan on 2012-04-05
> **priority said:**
> hello. i am trying to install Java 6.31 but i couldnt.. pls can u tell me how to do it ?? 

your green link doesnt work for me..

The green link is a straight forward guide to removing the previous version and installing the new one.
On the left side is the 32 bit instructions if you have a 32 bit machine and on the right side are the 64 bit instructions if you have a 64 bit machine like I do.

You must follow the instructions exactly as they are stated. It says to remove the previous version first.
If you have a 32 bit system, scroll down until on the left side you see 
**[SIZE=3][COLOR=#000000][SIZE=4][B]HOW-TO FOR 32 BIT UBUNTU**[/SIZE][/COLOR][/SIZE][/B].
It is down a good ways on that page. And if you have a 64 bit machine you should see **[SIZE=3][COLOR=#000000][SIZE=4][B]HOW-TO FOR 64 BIT UBUNTU**[/SIZE][/COLOR][/SIZE][/B] near the top on the right.

Both say to remove the older version first and there is a blue link that will take you to the instructions for removal.
Then you will go back up to just after the blue link you seen to remove the old version and follow the instructions from there.

It says to download the file ending in .bin and not the one ending in .rpm.
Then it is simply a matter of copying and pasting.
You must know where the downloaded file is for example:

[COLOR=Blue]sudo mv ~/Downloads/jre-6u31-linux-x64.bin /opt/java/64[/COLOR]
assumes that the file is in your Downloads folder. If not, you can find the file and right click on it and then click copy and then paste that into gedit (or any text editor).
That will show you the location of the file. If the file is not in your Downloads folder, you can simply copy and paste the command into gedit and modify it as needed.

Then when you are all done. Close Firefox and after a few seconds open it back up and enter ```
about:plugins
``` in the url bar at the top and if you see this you know you are all set:

**Java(TM) Plug-in 1.6.0_31**

 File:  libnpjp2.so

What is nice about this method is that you can perform these steps over and over without harm. If you do not see the above, you missed a step and need to start over.
I hope this makes it a little clearer.

---

### Post by priority on 2012-04-05
Sorry but really i am newbie and i am running Ubuntu 11.04 desktop x64 now..

yes jre-6u31-linux-x64.bin file is in /Downloads location but i dont know how to install it.. sudo mv command also doesnt work. it doesnt move anywhere.. 

from A to Z, what will i do exactly?

i cant open green link :/

---

### Post by Cavsfan on 2012-04-06
> **priority said:**
> Sorry but really i am newbie and i am running Ubuntu 11.04 desktop x64 now..

yes jre-6u31-linux-x64.bin file is in /Downloads location but i dont know how to install it.. sudo mv command also doesnt work. it doesnt move anywhere.. 

from A to Z, what will i do exactly?

i cant open green link :/

I am sorry but, I just provide the links to check and install the latest version of java. 

If you can't get the **sudo mv ~/Downloads/jre-6u31-linux-x64.bin /opt/java/64** command to work 
or the green link in my signature to open up, I don't know what to tell you.

If you can follow those directions to the letter you can get it to work.

My question is if you cannot get the green link to open, then how did you even see the **sudo mv ~/Downloads/jre-6u31-linux-x64.bin /opt/java/64** command? :confused:

---

### Post by priority on 2012-04-09
Hello again
Sorry writing late..

I saw sudo mv command in somewhere else while searching in google. They all mention to move to directory /lib .. 

I have .bin files in Downloads folder. Which I ve downloaded from java.com . ( 6.31 )

It s really annoying that why they don't give us .deb file ??

---

### Post by Cavsfan on 2012-04-09
> **priority said:**
> Hello again
Sorry writing late..

I saw sudo mv command in somewhere else while searching in google. They all mention to move to directory /lib .. 

I have .bin files in Downloads folder. Which I ve downloaded from java.com . ( 6.31 )

It s really annoying that why they don't give us .deb file ??

This method is how to manually update your java. Maybe you should stick with getting your java updates from the repositories.

[COLOR=Green]Before you go any further, enter this in the url bar at the top of your browser:

```
about:plugins
```If is says **Java(TM) Plug-in** and then a version number you should be OK and you do not need to do anything.
Since you did not remove the previous version of java as you could not open the green link 
in my signature.
If you do not see that, then go ahead and proceed with the stuff below.
[/COLOR]

These commands should work if you do not all ready have java installed.

During the installation press &#8216;OK&#8217; in the screen that appears within  the Terminal (see the below screenshot). 
You can do so by navigating  using the &#8216;Tab&#8217; key and once &#8216;OK&#8217; is highlighted in red, press &#8216;Enter&#8217;.

 [[IMG]http://www.multimediaboom.com/wp-content/uploads/2011/03/java-ubuntu-11.04.jpg[/IMG]]("http://www.multimediaboom.com/wp-content/uploads/2011/03/java-ubuntu-11.04.jpg")


```
sudo apt-add-repository &#8220;deb [[COLOR=blue]_http://archive.canonical.com/_[/COLOR]]("http://deb%20http://archive.canonical.com/") natty partner&#8221;

sudo apt-get update

sudo apt-get install sun-java6-jre sun-java6-plugin

sudo update-alternatives &#8211;config java
```As you can see from some of the posts on this thread, some people have updated their java 
successfully with these 2 links.

If you are really new to Ubuntu, you should stick with the easy stuff until you learn more about it.
I cannot explain it any more than I have.
Good luck!

---

### Post by priority on 2012-04-10
hello,

now i could open the green link u gave. i followed all steps explained in the link. but i think i couldnt install it :(

previously i have installed java v6 update 26 by using these commands :

> sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin
sudo apt-get install sun-java6-jdk


now i dont know how to remove it .. 

also 

should i remove open jdk and icedjava from ubuntu which installed by default ?

---

### Post by priority on 2012-04-10
ok i removed all java versions installed. now system is java free ..

now in green link :

> 8. Execute the file, with the following command.
Type (copy/paste):
sudo ./jre-6u31-linux-x64.bin

Press Enter.

this is ok. it executes the .bin file. but >

> Now the license agreement might appear (nowadays probably no longer!). If it does appear: press the space bar as many times, until you see the following text:
Do you agree to the above license terms? [yes or no]

Type:
yes

Press Enter. 

license agrement doesnt appear. 

i check > about: plugins in Google Chrome and java plugin doesnt appear there..

i dont know what s the problem :(

--------
your codes which u gave in page 2 :

> sudo apt-add-repository &#8220;deb [http://archive.canonical.com/](http://archive.canonical.com/) natty partner&#8221;
> Error: need a repository as argument

> sudo apt-get install sun-java6-jre sun-java6-plugin
>Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
E: Package 'sun-java6-plugin' has no installation candidate

> sudo update-alternatives &#8211;config java
>update-alternatives: error: unknown argument `&#8211;config'

---

### Post by Cavsfan on 2012-04-10
> **priority said:**
> hello,

now i could open the green link u gave. i followed all steps explained in the link. but i think i couldnt install it :(

previously i have installed java v6 update 26 by using these commands :



now i dont know how to remove it .. 

also 

should i remove open jdk and icedjava from ubuntu which installed by default ?

I am not sure what you should do, but this thread is simply supplying a link to check the java version and another with 
detailed instructions on how to download and install the latest version of Java.

I have tried to help you to the best of my ability. I think you should open a new thread in the help section of this forum 
with your problem.
Good luck.

---

### Post by priority on 2012-04-10
> **Cavsfan said:**
> I am not sure what you should do, but this thread is simply supplying a link to check the java version and another with 
detailed instructions on how to download and install the latest version of Java.

I have tried to help you to the best of my ability. I think you should open a new thread in the help section of this forum 
with your problem.
Good luck.


Thank you very much for your helps Cavsfan. i really appreciate.. good luck to you too..

---

### Post by Cavsfan on 2012-04-10
> **priority said:**
> Thank you very much for your helps Cavsfan. i really appreciate.. good luck to you too..

Thanks! I am sure someone will be able to help you out when you open a new thread with your problem.
There are a lot of knowledgeable people in this forum willing to help.

---

### Post by priority on 2012-04-10
Problem solved !

ok somehow now it s working :) i installed mozilla plugins .. also working in chrome.. 

thx for everything.. :)

---

### Post by Cavsfan on 2012-04-10
> **priority said:**
> Problem solved !

ok somehow now it s working :) i installed mozilla plugins .. also working in chrome.. 

thx for everything.. :)

Glad you got it working.

---

