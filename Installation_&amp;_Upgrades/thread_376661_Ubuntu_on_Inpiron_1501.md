---
title: "Ubuntu on Inpiron 1501"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by x2breakoffate on 2007-03-05
Hey, I just installed Ubuntu over Windows last night due to a Vista problem, go figure. Well heres my issue, I need my wireless working and I've seens these fixes like...

My question to you is what is sudo apt-get install linux-headers-'uname -r'? Honestly I have no idea what that means, what I do with it, what uname -r is.. please someone explain this to me and GREAT DETAIL, I MEAN GREAT

second I have no idea what a ndiswrapper 1.34 is... I'm sure I download it but where too? desktop? Dell drivers too on the desktop? What??? GREAT DETAIL, Linux newb, noob, nuub, spell it any way I'm still a newbie at linux.

once again where do I extract them? do I have to name them something special
ps: I'm still a newb at linux.

What in the heck is a ndiswrapper-version director. How and where do I place this thing and what is cd ndiswrapper. Still what is ndiswrapper.
how do i run and where is the source directory...
WHAT IS Run distclean in source directory. I'm confused of my "few words"

how do I run make and where, GREAT DETAIL

how do I run this make install in source directory as a root? DETAIL

How do I run the following in the directory or whatever, I'm still really really confused.

[B]1.Make sure you have the headers:
sudo apt-get install linux-headers-`uname -r`

2.Grab Ndiswrapper 1.34 from this link:
Ndiswrapper-1.34

3. Grab these Dell drivers from this link:
Dell Drivers

4. Go to the downloaded files and extract them:
tar -zxvf ndiswrapper-1.34.tar.gz
and
tar -zxvf DRIVER.tar.gz

5. The first will create the ndiswrapper-version directory. Change to that directory:
cd ndiswrapper-1.34

6. Once in the source-directory run:
make distclean

7. Then run:
make

8. making sure you are still in the source-directory, As root, run:
make install

9. Then run the following to install the drivers (change path if required):
ndiswrapper -i /DRIVER/bcmwl5.inf

10. $ ndiswrapper -m

11. $ sudo depmod -a

12. $ sudo modprobe ndiswrapper[/B]

Oh and my MP3's wont play, some kinda something needs to be downloaded like a plug in or something crazy cool like that.

And then I'm going to post or preferably get my question answered on how to get all my crazy neat windows program installs working like my photoshop cs2 cd, and macromedia studio 8, autocad 2007, mabye fable: the lost chapters, or maybe just windows stuff in general. Maybe a simple way of doing it to would be nice. Wow.. It seems so pointless but I dont know what draws me to this Ubuntu phehnomenon to love it so much. I think its great but I think .exe support for installs, or more support in thing in general would be nice. I like the idea of also being able to install things in a graphical environment. That'd be cool, this sudo this and that thing is making my nostrils hurt, thats how bad it is lol :) please help though, sorry for the head ache but please!!! I and my dell need help!

---

### Post by Oldstyl3 on 2007-03-05
I recently had problems with wireless capabilities.  You can find most of the files that you need from the package manager i.e. ndiswrapper(i think its 1.8 now)  look for the ndisw-utils as well.  You also need to look for the build essentials and kernel headers and install those.  Finally you need to look for the vendor specific drivers and unzip the .exe file you download into a directory of your choosing.  At least these were most of the problems that I came across, hope some of this helps.

---

