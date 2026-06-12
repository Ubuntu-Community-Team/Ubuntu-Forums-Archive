---
title: "How do I switch the window buttons back to the right without using commandline?"
date: 2010-04-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by alvevind on 2010-04-28
I've realized that I can never get used to the left position of the window buttons. 

The main reason for this is that I use Windows computer at work and the constant switching of desktop conventions is becoming too frustrating.

I also intend to try to convert some of my friends over to Ubuntu and I am convinced that they too would have an easier time converting if the window buttons remain on the right side as they are used to. I also want to enable them to install Ubuntu themselves using a short and simple step-by-step (mainly consisting of installing the package "ubuntu-restricted-extras" using Software Center).

Therefore my question:
How do I switch the window buttons back to the right side and back the standard order **without resorting to commandline** or downloading packages from non-standard repositories? 
(EDIT: i.e. if anything needs to be downloaded it must be available in the standard repositories.)

(Please read the question one more time before answering.)

--------------

EDIT:

* * * SOLUTION * * * 

What I ended up doing was:
1. System > Preferences > Appearance
2. Select the theme icon "New Wave" (it still has the buttons on the right side)
3. Click the button "Customize.."
4. Select tab "Controls" and scroll up and select value "Ambiance"
5. Select tab "Window border" and scroll up and select value "Ambiance"
6. Select tab "Icons" and scroll down and select value "Ubuntu-mono-dark"
7. Close. Close.
8. HAPPY!!!


* * * ALTERNATIVE SOLUTION * * *

1. Download modified theme from [http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz](http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz)
2. System > Preferences > Appearance
3. Click the button "Install"
4. Open folder "Downloads"
5. Select file "Ambience_Radiance-Right.tar.gz"
6. Click "Open"
7. Select the new theme "Ambiance-right"
8. HAPPY!!!!!!!

---

### Post by P4man on 2010-04-28
I know only one way which really is much more cumbersome than using the CLI. You need gconf-editor, but by default that is hidden in the gnome menu, so you have to right click the menu, edit menu, system tools and check configuration editor. Pwew, that was step one.

Then start configuration editor, browse to that key and manually alter its values.

Its doable, but are really you winning anything?

---

### Post by howefield on 2010-04-28
> **alvevind said:**
> How do I switch the window buttons back to the right side and back the standard order **without resorting to commandline** or downloading packages from non-standard repositories?

Choose another theme. It's only Ambiance and Radiance that have buttons on the left.

> (Please read the question one more time before answering. Please.)

Read the reply one more time before responding please.

---

### Post by bluelamp999 on 2010-04-28
Use Ubuntu Tweak - [http://blog.ubuntu-tweak.com/2010/03/14/ubuntu-tweak-0-5-3-released.html#more-597](http://blog.ubuntu-tweak.com/2010/03/14/ubuntu-tweak-0-5-3-released.html#more-597)

---

### Post by alvevind on 2010-04-28
> **P4man said:**
> I know only one way which really is much more cumbersome than using the CLI. You need gconf-editor, but by default that is hidden in the gnome menu, so you have to right click the menu, edit menu, system tools and check configuration editor. Pwew, that was step one.

Then start configuration editor, browse to that key and manually alter its values.

Its doable, but are really you winning anything?
Thanks. I will try this. But it does seem a bit cumbersome as you say.
EDIT: You were absolutely right, this was not easy or intuitive at all. The commandline is preferable to this.  

> **howefield said:**
> Choose another theme. It's only Ambiance and Radiance that have buttons on the left.
I chose the old theme "Dust" that is somewhat similar to the default, but even that one has the buttons on the left now. It seems the only fairly usable theme where the buttons remain on the right side is "New Wave". I really do not want to switch the theme itself unless it is to a more attractive theme.

> **howefield said:**
> Read the reply one more time before responding please.
I did :wink: 
(My intention with this was just to avoid standard answers that answer exactly the question I was not asking..)

> **bluelamp999 said:**
> Use Ubuntu Tweak - [http://blog.ubuntu-tweak.com/2010/03/14/ubuntu-tweak-0-5-3-released.html#more-597](http://blog.ubuntu-tweak.com/2010/03/14/ubuntu-tweak-0-5-3-released.html#more-597)
Unfortunately I could not find that tool neither using Ubuntu Software Center or Synaptic. As mentioned I want to avoid downloading software from outside locations and stick to what is available using the standard repositories.

But thanks anyway :-)

Anyone else with a possible answer to my question?

---

### Post by coffeecat on 2010-04-28
@alvevind, you don't have to use the CLI, you don't have to use gconf-editor (**EDIT: Especially not gconf-editor)**, and you don't have to use ubuntu-tweak. Everything you need is in the tin. Have a look at my post (no #2) in this thread. (Saves me typing it again. :wink:)

[http://ubuntuforums.org/showthread.php?t=1464472](http://ubuntuforums.org/showthread.php?t=1464472)

---

### Post by Dougie187 on 2010-04-28
[http://lifehacker.com/354925/arrange-the-window-buttons-in-gnome](http://lifehacker.com/354925/arrange-the-window-buttons-in-gnome)

---

### Post by coffeecat on 2010-04-28
> **Dougie187 said:**
> [http://lifehacker.com/354925/arrange-the-window-buttons-in-gnome](http://lifehacker.com/354925/arrange-the-window-buttons-in-gnome)

This is not a good idea.

Please see Mr Picklesworth's excellently argued post, the OP in this thread:

[http://ubuntuforums.org/showthread.php?t=1463878](http://ubuntuforums.org/showthread.php?t=1463878)

---

### Post by Calash on 2010-04-28
Right click on Applications and select Edit Menus

On the left panel scroll down and highlight System Tools.

Select the check box next to Configuration Editor

Press Close

Click on the Applications Menu

Scroll to System Tools

Select Configuration Editor

From this point follow the instructions for changing via gedit-conf


Honestly you are taking the harder path.  CLI is the easiest way to do this, followed by installing ubuntu-tweak.  

Most older themes should ask you what side you want the buttons on.  Try changing to a different theme then changing back and see if it prompts you.

Some themes may not have that information defined.  If this is the case you can get the buttons moved by picking a theme that sets them to the right, then pick your theme.

---

### Post by alvevind on 2010-04-28
> **coffeecat said:**
> @alvevind, you don't have to use the CLI, you don't have to use gconf-editor (**EDIT: Especially not gconf-editor)**, and you don't have to use ubuntu-tweak. Everything you need is in the tin. Have a look at my post (no #2) in this thread. (Saves me typing it again. :wink:)

[http://ubuntuforums.org/showthread.php?t=1464472](http://ubuntuforums.org/showthread.php?t=1464472)

Unfortunately I would have to "go out into the Internetz" to download this alternative theme using the web browser, and that is the other thing I am trying to avoid in this case. I only want to use what is available out-of-the-box or in the standard repositories :-(

---

### Post by alvevind on 2010-04-28
> **coffeecat said:**
> Please see Mr Picklesworth's excellently argued post, the OP in this thread:

[http://ubuntuforums.org/showthread.php?t=1463878](http://ubuntuforums.org/showthread.php?t=1463878)

Thanks! It sort of kind of works although it does not really. :neutral:

I had to read the Mr Pickesworth post several times cause the "solution" is so counter intuitive and really is not a full solution only an attempt at a workaround.

I selected "New Wave" as the theme, then clicked "Customize" then chose the "Radiance" window border.

The window border is now as I intended but everything else is "New Wave" and it does not look too consistent :-?

So I am still looking for a good solution to my problem!
:^o

EDIT: Why oh why could not Canonical simply provide a user selectable theme that is identical to the default Radiance but with the buttons in the standard position?

---

### Post by coffeecat on 2010-04-28
> **alvevind said:**
> Thanks for creating the new alternative theme! Unfortunately I would have to "go out into the Internetz" to download this, and that is the other thing I am trying to avoid in this case. I only want to use what is available out-of-the-box or in the standard repositories :-(

**Please** read my linked post again. ](*,)](*,)I did not create that theme. I posted an easier way of getting the buttons on the right using the GUI. Exactly what you want.

Oh dear, oh dear, oh dear. :cry:

---

### Post by Calash on 2010-04-28
Hold the Alt key and press the F2 button

Past the following in the field

```

gconftool-2 --type string --set /apps/metacity/general/button_layout ':minimize,maximize,close'

```

Press Run


On a side note, it seems like you are trying to make a point.  This is really not the place to do it.  We are all users just like you who volunteer our time to try and help out fellow Ubuntu users.  If you are not willing to follow the instructions people are giving you to fix the problem then you probably should not be asking.

Check this link for more information

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633)

---

### Post by coffeecat on 2010-04-28
> **alvevind said:**
> Thanks! It sort of kind of works although it does not really. :neutral:

It works COMPLETELY. You haven't done it properly.

I hate repeating myself but:

> **coffeecat said:**
> @alvevind, you don't have to use the CLI, you  don't have to use gconf-editor (**EDIT: Especially not gconf-editor)**,  and you don't have to use ubuntu-tweak. Everything you need is in the  tin. Have a look at my post (no #2) in this thread. (Saves me typing it  again. :wink:)

[http://ubuntuforums.org/showthread.php?t=1464472](http://ubuntuforums.org/showthread.php?t=1464472)

My post**[SIZE=7] #2 [/SIZE]**[SIZE=7][SIZE=1]in that thread.[/SIZE]
[/SIZE]

---

### Post by Curtiss on 2010-04-28
You can do this the easy way go here and download Ubuntu Tweak. There's a setting in there to change the button layout. Works great in Lucid RC 64 bit.

[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

---

### Post by alvevind on 2010-04-28
> **coffeecat said:**
> **Please** read my linked post again. ](*,)](*,)I did not create that theme. I posted an easier way of getting the buttons on the right using the GUI. Exactly what you want.

Oh dear, oh dear, oh dear. :cry:

You are quite right! 
Please excuse my confusion.
There was such a torrent of answers in a very short time that I did not read properly and also did not execute the action properly.
(By the way the "Human" theme is gone in my fresh-today install.)

What I ended up doing was:
1. System > Preferences > Appearance
2. Select the theme icon "New Wave" 
3. Click the button "Customize.."
4. Select tab "Controls" and select value "Ambiance"
5. Select tab "Window border" and select value "Ambiance"
6. Select tab "Icons" and scroll down and select value "Ubuntu-mono-dark"
7. Close. Close.
8. HAPPY!!!

Thanks to everyone helping out!

But I am still interested in an even easier way if it exists!

:popcorn:

---

### Post by alvevind on 2010-04-28
> **Calash said:**
> Hold the Alt key and press the F2 button

Past the following in the field

```

gconftool-2 --type string --set /apps/metacity/general/button_layout ':minimize,maximize,close'

```

Press Run


On a side note, it seems like you are trying to make a point.  This is really not the place to do it.  We are all users just like you who volunteer our time to try and help out fellow Ubuntu users.  If you are not willing to follow the instructions people are giving you to fix the problem then you probably should not be asking.

Check this link for more information

[https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633)

I appreciate your opinion but I disagree with your interpretation.

I was honestly not trying to make a point, only trying find a solution to my specific dilemma (which excluded the commandline). 

As it turned out such a solution did indeed exist!

---

### Post by Starks on 2010-04-28
mwbuttons.

nuff said.

[http://www.webupd8.org/2010/03/mwbuttons-complete-gui-for-customizing.html](http://www.webupd8.org/2010/03/mwbuttons-complete-gui-for-customizing.html)

If you can't be bothered to enter 3 simple commands, there is no hope for you.

---

### Post by alvevind on 2010-04-28
> **Starks said:**
> If you can't be bothered to enter 3 simple commands, there is no hope for you.

I think you misinterpreted the "fine print" of the purpose of this thread. (I do not want to download anything unless it is from the default Ubuntu repositories.)
But thank you for your optimistic assessment of my future prospects!
:lolflag:

Anyway. Thank you Stark, coffeecat and everyone else for contributing to this thread. I have an acceptable solution now so I do not need more solutions unless they stick by all the requirements stated in my first post and are easier to perform than the solution I already have.

---

### Post by mc4man on 2010-04-28
> are easier to perform than the solution I already have.
The one you have is quite easy once you get the idea.
Being no fan of ubuntu-tweak would never suggest - the mentioned mwbuttons is as easy as appearances and a bit more configurable

If it becomes a deb install will let you know - though setting up as a menu item only take a min or so.

---

### Post by linuxman94 on 2010-04-28
Here is the easiest way I have found to change the window button's positions.  It is in the form of a python scrip.  Once you download it, right click it and select 'properties' then the permissions tab.  Check the box to allow executing it. Close the window and double click.

---

### Post by qyot27 on 2010-04-28
I really don't see how enabling the System menu under Applications is more cumbersome than the command-line (aside from the usual often-cumbersome nature of GUIs in general)...but then again, I *always* make sure to edit my menus and enable Applications->System every time I install Ubuntu, as a matter of principle.

---

