---
title: "How do I (editing menu.lst)?"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by quark_77 on 2007-02-03
I have installed the generic version of Edgy, which by default adds three options to menu.lst:
[LIST]
[*]Ubuntu-[kernel]-generic
[*]Ubuntu-[kernel]-generic (recovery console)
[*]Ubuntu, memtest86+
[/LIST]
under debian automagic, with by XP install below that. My question is, besides changing the root password (already done that!), can I remove the recovery console from this list and how do I add a console version of Linux to it i.e. one that doesn't load GDM? The reason for doing this is to become more au fait with the console (and whilst I'm doing fairly well I'd rather not have root access enabled all the time).

Thanks in advance!

---

### Post by mikewhatever on 2007-02-03
I think you can just comment them out (put # in the beginning of the line). Check the [GRUB PAGE]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by Herman on 2007-02-03
Hello quark_77,
mikewhatever is correct, 'commenting' a line by 'hashing it out' in menu.lst makes the computer ignore that line.

I don't understand why you would want to do it that way though, I mean, doing it at startup seems like 'overkill' to me.

Why not just boot the normal way and try pressing 'Ctrl' + 'Alt'  + 'F1', that will give you a 'tty', you can log in with your username and password then, and practice Linux commands there.
One that's kind of neat is when you type the following,
```
w3m www.google.com
```That gives you a command-line type of web browser, try it! You can't use your mouse, but you can move the cursor around with keys on your keyboard and type. It might take some experimenting to become skilled at using it.
Type 'q' for quit, to exit w3m, then 'y' for yes.
When you are finished using the tty, type 'exit' to log out of the tty.,just press 'Ctrl' + 'Alt'  + 'F7' to return to the normal G.U.I.

There are tty's for F2, F3, F4, F5, and F6. (When those keys are pressed simultaneously with 'Ctrl' + 'Alt'
'Ctrl' + 'Alt'  + 'F7'  keys return you to GUI mode.

You can also type 'bc' for a terrific text-mode calculator that can handle a lot of digits. One of the great features of this calculator is you can press your 'up arrow' key to scroll back to previously entered operations. Very handy and convenient. You will discover more about bc when you start practicing with it. When done, type 'quit' to get back to your command prompt.
```
bc
```

Another little trick is to type 'cal' for a calendar. Today's date will be highlighted.
```
cal
```

We can do all these things in a terminal too, but a tty is easier on the eyes because it has a black background. You can change the color of your terminal by right-clicking on an open terminal window and then click 'edit current profile', and in the 'Colors' tab, remove the check mark from the square for 'Use colors from system theme'. Then you can choose your own text color and background color for your terminal. If that isn't enough for you, you can click the 'effects' tab, and choose a background image, or select the radio button for 'transparent background', and even set the opacity with the slider under there.

There are lots of good linux tutorials already available, I imagine you already have one or more you will be learning from. One of the best is by one of our own Ubuntu Web Forum members, Kryal, '[terminal for beginners]("http://www.ubuntuforums.org/showthread.php?t=73885&highlight=terminal+beginners")'

Have fun!  :)
Regards, Herman

---

### Post by quark_77 on 2007-02-08
Hi Herman,

The main reason for using grub/menu.lst was that I couldn't think of any way not to load gdm, but anyway, I will have a look at the various programs etc. I've not got a tutorial as I've used windows for a while with ports of gcc and various command line tools, so once I realised man "program name" tends to explain how to use said program I was ok... just about!

Having said that, a) Linux command line is more powerful than windows (even with powershell) and b) I'd like to use the server version but not the whole desktop eventually, hence the need to be able to use the command line without the good old windows habit of running back to a fs explorer like nautilus!

I followed the grub/security tutorial to set an admin password for booting Ubuntu recovery mode.

Anyway, thanks everyone.

---

### Post by Herman on 2007-02-08
Hello again quark_77,
I think it's great to learn Linux commands, we all should be learning them as much as we can, it's great fun.
I am not a college boy myself, I'm more of an outdoors type, and maybe not the kind of person you would expect to be interested in computers and in Linux. I drive big trucks, spent seven years working on small ships, tug boats and fishing vessels, and have done hard work on farms. In the real world you may see me swinging a sledge hammer or operating a jackhammer or shoveling concrete.
So how does the average man on the street or in the bush (or woods if you are Canadian or American) go about getting started learning Linux? 
Read man pages? ...type 'help'? 
Well, I don't know about you, the 'man' pages are a great help, but where is the tutorial on how to read man pages?
Honestly, if we haven't got someone around with a little Linux experience to help get us started, it's a challenge to get started with Linux.
A good tutorial does help. Did you click on the link to kyral's tutorial I included in my previous post? Here it is again in case you missed it, Kyral's '[terminal for beginners]("http://www.ubuntuforums.org/showthread.php?t=73885&highlight=terminal+beginners")'


The first tutorial I tried was this one, it's a Unix tutorial, Unix is the language that Linux is based on, so the basic commands are the same. 
[http://www.ee.surrey.ac.uk/Teaching/Unix/  ]("http://www.ee.surrey.ac.uk/Teaching/Unix/")
I spent some time working my way through the exercises in that one. I still look things up in that one often. I didn't complete the whole thing though, I should make an effort to do so.

Another one I partially completed was this one, which is also very good, [http://www.linuxcommand.org]("http://www.linuxcommand.org/")

And here's another one I started but only got part way through, (although I look things up in it quite often), [Rute User's Guide and Exposition]("http://rute.2038bug.com/rute.html.gz")

All of the above are great tutorials. They don't all apply directly to Ubuntu, the Rute one is more about Red Hat Linux, but most of the commands will work the same in Ubuntu as well.

To make Linux really come to life, you have to create some files and start using it for your everyday chores. Tutorials are just dry reading unless you do that.

It's amazing what we can do in Linux with just a plain text file. 
I'm keeping a plain text file in my computer that will be my diary for the whole year. It's called '2007_log.txt'.
It's easy to make a diary out of a plain text file. my favorite text editor is 'Gedit', ('Applications'-->'Accessories'-->'Text Editor').
The Gedit text editor is ideal for making a diary with, because it has a feature for adding the date easily, I just go 'Edit'-->Insert Date and Time.
In this diary, I have daily entries for lots of everyday things I want to be able to remember and look back up again. I type in all kinds of information, like a new joke I heard, a great new recipe I managed to get hold of after a tasty meal, or just the main events of each day, what work I got done, how much I got paid, how much I lent someone, etc. So as you can imagine, it's a huge file, with everything all jumbled up together. Well, it's all in chronological order of course. But how do I find things in it?

I use grep, that's how. 

For example, I type in information from my petrol receipts I get from service stations when I fill my car up with petrol, ('Gas' if you are American or Canadian).
The trick is, to make each line with a petrol receipt in it begin with the heading, 'petrol:'
for example,

Expenses: Petrol: $ 67.82 for 56.66 litres @ 119.7 at (Service station), Townsville, 09:28 EST.

I also use the heading 'Expenses' too, so later on I can grep all my expenses, including groceries and all kinds of things.
I try to stick to the same format each time (for each entry). 
A grocery docket will be headed 'Expenses: Groceries:

Now here's the good part. Whenever I want to see all my petrol expenses, I just open a terminal and type 'grep 'Petrol' 2007_log.txt', and I have added the options --color -in to make it a little more interesting. I got those options by looking up 'grep' in a man page and trying them out until I found some options for grep that I like.

```
                   herman@rocky:~$ grep --color -in 'Petrol' 2007_log.txt               
```This prints me out a complete list of all my petrol expenses for the whole year. I can see at a glance how much money it cost me to go on a recent long trip. And I can see at a glance which service stations had the lowest prices too! 

Another option to use with grep (from the man page), is -R (recursive), 
For example,
```
herman@rocky:~$ grep --color -inR 'Petrol' /home/herman    
```  -R recursive, meaning search the whole /home/herman directory for files containing 'petrol' or 'Petrol', and  (-i ignore case, -n number, include the line number before the line, prints all lines with Petrol and petrol, hilited in red).

grep can also 'grab' any number of lines around the word I am searching for, or before or after the specified word or phrase. 
For example, if I want to look up what happened on a particular day, I can either just open my text file and scroll to it, or I can use grep. 
This one, using the -A option (for '_A_fter'), lists 8 lines after the date 'Wed 03 Jan'. 
The -B option would have listed the 8 lines _B_efore line containlng the date 'Wed 03 Jan'. 
Just a number 8 with no option shows the line with the date 'Wed 03 Jan' in the center of the other lines.
```
                   herman@rocky:~$ grep -A 8 'Wed 03 Jan' 2007_log.txt
```I can equally easily grep a joke or a favorite recipe or anything else in my computer, so grep is a very useful command to practice with.
Here are another couple of possible uses, 
```
herman@rocky:~$ grep -inR 'Loans: Peter:' 2007_log.txt               
``` ```
herman@rocky:~$ grep -inR 'Debts: Paul:' 2007_log.txt    
```As you can imagine I could easily grep 'Peter' for a complete list of all my dealings with Peter so far this year. Or, if I grep 'Loans', I would have a complete list of all the money I lent people all year. It can be kind of handy to be able to recall information like that easily sometimes. :)

I recommend other beginners should start a diary in a plain text file too. Put in it anything you like, it's an excellent file to practice Linux on and serves a useful purpose at the same time.

Have fun, Regards, Herman :)

---

### Post by quark_77 on 2007-02-10
Once again, Herman, fantastic set of links. I quite agree man pages tell you how to use a program but not what the options might be or how we should set things up, chmod and chown are prime examples... Yes I have tried his tutorial, right from the beginning. It's fantastic.

One problem I have, which I think is related to my ATI drivers [fglrx] is: when I press 'Ctrl+Alt+F[1-6]' my gui goes down and I get a mess of colours, making me think my graphics card has given up. 'Ctrl+F7' brings me back to the gui, luckily! Any ideas? I've used gnome-terminal set to full screen which is close enough.

I moved to Linux for a number of reasons. Firstly, Windows costs too much, especially here in the UK. The American prices don't translate by exchange rates; we are charged more. Linux is free and more secure & stable. Secondly, as I study languages & mathematics, it's useful to have UTF-8 support and proper character insertion for the characters not on my keyboard, which Windows simply lacks.

I must play with grep... I save scraps of web pages [foreign language] either with scrapbook [firefox addon] or as plain text files depending on whether I want to preserve images / formatting.

Anyone can learn to use Linux, so no, it doesn't surprise me. In fact, wielding sledgehammers and running Windows would be an interesting combination...

Thanks again!

---

### Post by confused57 on 2007-02-10
Herman's advice and his excellent website have saved me countless times.

I just wanted to mention a similar problem I had when I installed Gentoo:
> One problem I have, which I think is related to my ATI drivers [fglrx] is: when I press 'Ctrl+Alt+F[1-6]' my gui goes down and I get a mess of colours, making me think my graphics card has given up. 'Ctrl+F7' brings me back to the gui, luckily! Any ideas? I've used gnome-terminal set to full screen which is close enough.

When I would press Ctrl+Alt+F1 from the GUI, I would get a monitor out-of sync...my fix was to disable framebuffer support in the kernel boot line, then I had no problem with switching to a console.
   I'm not sure how to do this in Ubuntu, but the command:
```
sudo dpkg-reconfigure xserver-xorg
```
allows you to select whether you want to use framebuffer support, I always select "yes" and haven't had any problems.

May have absolutely nothing to do with your problem, but thought I'd mention it.

---

### Post by Herman on 2007-02-10
> One problem I have, which I think is related to my ATI drivers [fglrx] is: when I press 'Ctrl+Alt+F[1-6]' my gui goes down and I get a mess of colours, making me think my graphics card has given up. 'Ctrl+F7' brings me back to the gui, luckily! Any ideas? I've used gnome-terminal set to full screen which is close enough.  quark_77,
:-k Hmmm, I don't know might be the problem there. confused57 might have the answer.

 I have an ATI card too and mine has always worked normally when switching to a 'tty'. I'm no expert on the X-server by any means, but I did make a web-page called [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html"). It's really just designed for beginners who get dumped at the shell after an installation, if their X-server fails to initiate. It's only meant to be enough to guide them through the process and introduce them to the basics, (in an 'emergency'). You might find something in links off my web page that might help you improve your graphics though. I link to some other sites that are more advanced than mine.

I might find out more about framebuffer support so I can add a comment to the appropriate spot in that web page now that confused57 has brought the subject to our attention. Thanks confused57! :)

I just had a look at my own /etc/x11/xorg.conf file and it looks like I am just using the generic ati driver at the moment. I do have the fglrx driver in one of my installations, probably Dapper. (I'm running Edgy at the moment, and haven't taken the time to install the fglrx driver yet).

 In any case though, I am sure a terminal expanded to full size will do just as well if not better than a 'tty'. What I do myself, since I use the terminal frequently, is right-click on the line for it in 'Appliccations'--> 'Accessories'-->'Terminal', and click 'add this launcher to panel. And I do the same with the text editor, so they are both handy and quick to access.

Regards, Herman

---

### Post by confused57 on 2007-02-10
Herman,
    Rather than going through reconfiguring the xserver, wonder if you can just add a kernel option, by press "e" at the bootup grub menu & add something like vga=normal or nofb...then see if it makes a difference when switching to a console from the gui?  I may be way out in left field on this one, but it's probably worth trying for someone with this problem.

---

### Post by Herman on 2007-02-10
confused57,
Darn it, I think you're right again! :)
Now that you have reminded me, I remember that, of course the GUI isn't in use when we're in 'tty', which is probably the main reason why 'tty's are  still with us.
We can boot up with kernel options by pressing 'e' at the grub menu, as you say, that's right. And if we want to make that change permanent, we can edit our menu.lst file, so our computer will automatically boot with those options all the time.  
And if we want to make the menu.lst entry permanent, we edit our  [defoptions]("http://users.bigpond.net.au/hermanzone/p15.htm#defoptions") in our automagic kernels list. 
I added a great link to my Grub Page under defoptions, about how to change boot-up resolution, here it is,  **[HOWTO: Change bootup resolution]("http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters"), by **[Indras]("http://www.ubuntuforums.org/member.php?u=126305")
> I've seen a few questions about this on the forums, so I've decided to write a full-fledged tutorial on how to set this up in Ubuntu. This will show you how to change your screen's resolution while booting, during usplash, and at any time one one of the text consoles (by pressing CTRL+ALT+F1 through F6). I'll try to make this as friendly as possible for newbies, and I'll make sure to explain all acronyms and abbreviations at least once.
I think that would be just the link quark_77 should read to find out how to fix the problem. 
quark_77, after reading that link, I would test some likely options using confused57's method for editing the grub menu, then you could make that change permanent in the two ways I just described. If you aren't sure how to edit your menu.lst, please click on my third sig link. It's all explained there.

Thanks again, confused57, you are a genius! :guitar:

Hey, we've done the full circle and arrived back at the title of this thread: "How do I (editing menu,lst)?"

He-he, Regards, Herman :)

---

### Post by confused57 on 2007-02-11
It was just an idea I thought of from my experiences with Gentoo, which by the way, makes me really appreciate the ease of use of Ubuntu...last night while doing an update in Gentoo, halfway through the update, it stopped after throwing a "Call Stack?"  error during compilation...so I just closed the terminal & thought I'd just surf a little in Gentoo.  Gnome & X was completely "borked", rebooted, gdm wouldn't even come up...got out my Gentoo handbook notes, switched to a console, 3 hours later(most of it was just portage doing it's compiling, running test suites, resolving dependencies,etc), I had everything working again...I'm sure a lot of my problems were due to user error, but I usually learn the most when trying to repair things.
Did I mention I really appreciate Ubuntu?

---

### Post by quark_77 on 2007-02-12
Hi Herman, confused57,

Thanks once again, now I have solved the problem. I booted using grub and as herman suggested played around with the kernel boot options.

The default options are: ro quiet splash. This setup produces the strange screens in place of ttys.
After a certain amount of fiddling I changed this to: ro quiet vga=0. the vga option isn't important, and I can add nofb into the mix without problems and remove the quiet option without problems. The problem appears to be the inclusion of the splash option to launch usplash. If I put this in in any combination I can't use the ttys. If I omit it, I can access them without any problems.

Once again, thank you all very much, I now know far more about grub than I thought possible AND I can play with the command line...

Cheers

Quark_77

---

### Post by mayerf on 2007-04-02
> **quark_77 said:**
> Hi Herman, confused57,

Thanks once again, now I have solved the problem. I booted using grub and as herman suggested played around with the kernel boot options.

The default options are: ro quiet splash. This setup produces the strange screens in place of ttys.
After a certain amount of fiddling I changed this to: ro quiet vga=0. the vga option isn't important, and I can add nofb into the mix without problems and remove the quiet option without problems. The problem appears to be the inclusion of the splash option to launch usplash. If I put this in in any combination I can't use the ttys. If I omit it, I can access them without any problems.

Once again, thank you all very much, I now know far more about grub than I thought possible AND I can play with the command line...

Cheers

Quark_77

Thank you for the description. 

I have a ATI radeon 1950 - card and I have had the same trouble with accessing the console due to randomly colored lines. I compiled the kernel 2.6.20 by myself and used the proprietary ati-driver, dont know if this is important (but maybe for google to find this page :) )

Thanx & greets,
Frank

---

### Post by quark_77 on 2007-04-03
Hi mayerf,

I'm not sure why this happens, I just know usplash kills my ttys - I've also compiled 2.6.20(.4) and fglrx - I've not tried enabling usplash again but I have a sneaking suspicion it would work...

Glad I could help.

Quark_77

---

