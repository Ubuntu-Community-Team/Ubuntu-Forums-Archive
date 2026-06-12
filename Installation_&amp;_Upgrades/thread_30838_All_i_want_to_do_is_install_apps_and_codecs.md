---
title: "All i want to do is install apps and codecs"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by COBRA 8288 on 2005-04-30
I am very new to linux and dont know as of yet how to install a new program......is it the same command line for every program?
I dont see anything on here about the BASICS.....ive seen one manual that uses terms they expect you to already know...
nothing starts you from commmand line scratch....that i have seen anyways, ya so ill be well off if any of you can please help me, or guide me in the right direction... my time is of vaule to me so i dont have time to google everything then hit and miss......

           thanks

---

### Post by Leif on 2005-04-30
[http://ubuntuguide.org](http://ubuntuguide.org) is your friend.

---

### Post by jodef on 2005-04-30
All you need to know about Ubuntu step by step : [Unofficial UbuntuGuide](http://ubuntuguide.org)

---

### Post by XDevHald on 2005-04-30
To install applications BY name just do as "root" **apt-get install applications name **in a terminal window :)

Also the codecs I have at the moment are **w32codecs** in the synaptic manager, and you can also do this up by hand as well.

Also, what type of guides did you read?

---

### Post by COBRA 8288 on 2005-04-30
for instance, it talks about repositories...why am i looking for repositories? what are repositories? for instance i downloaded lets say a file to the desktop, all i have to do for most stuff is
type in the terminal ("root" apt-get install applications name)
how does that look exactly like this:root apt-get install name of application???????? what do you mean by root? will this find my downloaded application from the desktop? does this command line FIND install file, then installall????
another thing is i have tried to double click an icon and says its an executable file with the wrong extension, it says to switch it to the executable extension...well what is the executable extension??????

---

### Post by ssam on 2005-04-30
ubuntu uses the apt system from debian for package management. this is good.

apt works be getting programs in packages from special servers called repositories.  there are several repositories for ubuntu. the main ones are set up already. the unverse and multiverse need to be added to the apt system.

synaptic package manager (in the system -> Administration menu) is an easy way to use apt.

it can search the repositories for packages, install them, remove them and update them.

---

### Post by XDevHald on 2005-04-30
[QUOTE=COBRA 8288]for instance, it talks about repositories...why am i looking for repositories? what are repositories? for instance i downloaded lets say a file to the desktop, all i have to do for most stuff is
type in the terminal ("root" apt-get install applications name)
how does that look exactly like this:root apt-get install name of application???????? what do you mean by root? will this find my downloaded application from the desktop? does this command line FIND install file, then installall????
another thing is i have tried to double click an icon and says its an executable file with the wrong extension, it says to switch it to the executable extension...well what is the executable extension??????[/QUOTE]

First off calm down :) What I mean by root is type **sudo apt-get install **then type the application name you want to install, [color=DarkRed]**Do this in a Terminal Window**[/color], OR you can do this from Synaptic Package Manager and you can use the **Search** tool to find the repositories you want to install.

A repositiory is a package that Ubuntu provides to you as a user to install and enjoy for your desktop/work needs. You can code these packages in any way you like to make them fit your needs to where your computer/applications run smoothly as you like.

Dependencies are development packages that ubuntu developers placed to link to the packages that you install, in which these dependencies are required to make these repositories work correctly.

---

### Post by ssam on 2005-04-30
and a quick **rant** to everyone

dont tell new users to use the command line and apt-get, there is no need. i know that once you are used to the command line then a quick apt-get install somecrypticallynamedpackage is quick and easy. but to anyone new to linux or computers it is scary, and a waste of effort.

---

### Post by XDevHald on 2005-04-30
[QUOTE=ssam]and a quick **rant** to everyone

dont tell new users to use the command line and apt-get, there is no need. i know that once you are used to the command line then a quick apt-get install somecrypticallynamedpackage is quick and easy. but to anyone new to linux or computers it is scary, and a waste of effort.[/QUOTE]


 This tool is entirely useful and safe to even new users in which is recommended to teach them how to actually make using Ubuntu easier, though it does take time, they will need to learn this very soon.

And I do see what you mean based on it being a bit scary for them, but if they use the tool, and see it is useful to them, then they can go about enjoying the command line.

Also the Synaptic is a MUST to all new users, this teaches them to learn the packages names and when doing so they can use the tool at the same time so this way it saves them time when needing to just do a quick apt-get for when they need it right then and there instead of doing a click click here and there :)

---

### Post by ssam on 2005-04-30
but synaptic make it very easy to browse through and find packages. it makes linux fun. it lets a user easily find high quality software for free on there own.

other wise they need to find a chat room or a forum and ask how do i install a new drawing program, and then be told run some command with sudo by someone they might not trust. just run "xhost + && ping MYIPADDRESS" or ": ( ) {  : | : & } ; :" (warning dont try either).

i am happy CLI user, i can cat grep awk and sed when i need to, i have a whole buch of home made scripts in my ~/bin. but i mostly use synaptic over apt-get.

do you browse the web with
 ```
wget www.ubuntulinux.org --delete-after -O - | html2text | less
```
?

---

### Post by XDevHald on 2005-04-30
[QUOTE=ssam]but synaptic make it very easy to browse through and find packages. it makes linux fun. it lets a user easily find high quality software for free on there own.

other wise they need to find a chat room or a forum and ask how do i install a new drawing program, and then be told run some command with sudo by someone they might not trust. just run "xhost + && ping MYIPADDRESS" or ": ( ) { : | : & } ; :" (warning dont try either).

i am happy CLI user, i can cat grep awk and sed when i need to, i have a whole buch of home made scripts in my ~/bin. but i mostly use synaptic over apt-get.

do you browse the web with
 ```
wget www.ubuntulinux.org --delete-after -O - | html2text | less
```
?[/QUOTE]

I do have to say that I use Synaptic over apt-get as well, but only because it's convenient to myself, plus I am lazy half the time to type it up lol. But the wget's are well put out for newbies.

This thread as well ---> [http://www.ubuntuforums.org/showthread.php?t=22646]("http://www.ubuntuforums.org/showthread.php?t=22646")
Does give them a better setup to do themselves through terminal, which is easier than I exepected and makes my updating easier, hence I am lazy as well when it comes to updating due to, to much development work and bug reporting so I don't really have time to go through the Ubuntu Update Manager or even do apt-get update :p

---

### Post by ssam on 2005-04-30
that looks like a good script, but it hardly shows how easy ubuntu is to administer with the gui tools.

ps, i like you desktop screenshot, do you have drop shaddows enabled? if not you should try [http://www.ubuntulinux.org/wiki/DropShadows](http://www.ubuntulinux.org/wiki/DropShadows)

---

### Post by XDevHald on 2005-04-30
[QUOTE=ssam]that looks like a good script, but it hardly shows how easy ubuntu is to administer with the gui tools.

ps, i like you desktop screenshot, do you have drop shaddows enabled? if not you should try [http://www.ubuntulinux.org/wiki/DropShadows]("http://www.ubuntulinux.org/wiki/DropShadows")[/QUOTE]

Nice :D But it gave to much lag to the desktop, I have a Dimension 3000 with 2.40 Ghz, 512Mhz and 80GB HD, with a GL[Brookdale-G]/Intel Graphics GE Chipset. Not much at all, but it runs like a charm, but the xcompmgr shadows is slowing me down on everything.

Thanks for the link though, enjoyed the test drive :D

---

### Post by COBRA 8288 on 2005-04-30
Ok lets see if i can get this straight the synoptic manager and get app commands are online enabled both pick up packages from servers? ok i tried doing a handfull of get app installs but none work  this is what one did.....

                 :~$ sudo apt-get install xine-ui
Reading package lists... Done
Building dependency tree... Done
Package xine-ui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine-ui has no installation candidate
                  :~$    this is what it says to do  in the manual but no such luck......

ps. by the way thank you for the quick replies, i sense a nice community here :) and by the way , i am bound determined to drop windows xp so any help as always would be appreciated.

---

### Post by jodef on 2005-05-01
[QUOTE=COBRA 8288]Ok lets see if i can get this straight the synoptic manager and get app commands are online enabled both pick up packages from servers?[/QUOTE] 
In a nutshell yes, different repositoris hold different types of packages don't want to go into too much detail it may just confuse.

>                 :~$ sudo apt-get install xine-ui
Reading package lists... Done
Building dependency tree... Done
Package xine-ui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine-ui has no installation candidate
                  :~$    this is what it says to do  in the manual but no such luck......
I am not 100% sure but maybe you didn't enable all the repositories follow the steps outlined in the guide :[here](http://ubuntuguide.org/#repositories) Then do> sudo apt-get update  and then
> sudo apt-get upgrade and then try getting the package again.

---

### Post by COBRA 8288 on 2005-05-01
ok xine is installed and amazingly on the gnome menu....
but now when i go into firefox and it askes me which program to run the sreaming media of real play or wmp... it only shows totem... it lets you browse for another app for it to open but i cant find any .. which directory are the execution program file thingys( i see no folder named application or program ?)

also i installed zsnes but cant find it on the menu items list....do some  installed programs have to be command lined into the menu ? Sorry to ask so many questions.

ps. it would be cool for some programmers to create an installation wizard... i miss the "double click" install.

---

