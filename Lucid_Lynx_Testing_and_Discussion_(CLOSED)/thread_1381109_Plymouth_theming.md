---
title: "Plymouth theming ?"
date: 2010-01-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2010-01-14
Just thought that as folk are starting to use and play with Plymouth we should have a thread purely for theming it.

Just to state my Plymouth install is straight form upgrades - I did not install by myself, everything through the repo's.

I am trying to get one of the themes from this page to go, but having problems :-

[http://gitorious.org/oskude-plymouth-themes](http://gitorious.org/oskude-plymouth-themes)

The first thing I noticed is that you have to have git (obviously) and inkscape installed to build his images.

Then the directories that he uses differ from the way Plymouth has installed on my Lucid. In his readme he uses /usr/share/plymouth, but on lucid it is installed to /lib/plymouth.

After a bit of Google-ing I have come up with this to install the theme :-

sudo plymouth-set-default-theme space-sunrise --rebuild-initrd

BUT I get this :-

update-initramfs: Generating /boot/initrd.img-2.6.32-10-generic
cp: cannot stat `/lib/plymouth/ubuntu-logo.png': No such file or directory

(I have renamed the ubuntu-logo.png file as I thought that this was causing problems with changing the theme)

So my questions are, can plymouth be themed in its current state in Ubuntu, if so how, if not why not?

Just to update - tried again with ubuntu-logo.png file restored and operation completes

BUT on shutdown I can see the animation start (shuts too quick for it all to play)
yet starting again I get the usual Ubuntu !!

---

### Post by celticbhoy on 2010-01-14
OK to answer my own questions - YES Plymouth is theme-able inUbutnu as of now.

How to do it - quite easy really 

1) from terminal type

sudo plymouth-set-default-theme --list

you will then get a list of the themes installed by default (solar is nice)

2) enter

sudo plymouth-set-default-theme solar --rebuild-initrd (replacing solar for the theme of your choice)

And thats it. I think that the theme that I downloaded just doesn't work with this version of Plymouth or not at all.

If you look in /lib/plymouth/themes then you can go in and have a look at each.

The only other thing is the ubuntu logo I mentioned earlier - it has to be there (although you can change it for one of your own)

---

### Post by celticbhoy on 2010-01-14
For those interested there is a guide to theming Plymouth here :-

[http://brej.org/blog/?s=plymouth&x=0&y=0](http://brej.org/blog/?s=plymouth&x=0&y=0)

---

### Post by ranch hand on 2010-01-14
Oh my, good work.  Thank you for this.

I did not look at the theme you were trying to use but can you not just take the image and replace the one in solar with it?

That worked very slick for an image that I had and used.

---

### Post by cecilpierce on 2010-01-14
tried two different themes on the list, says "could not start splash : no such file or directory", before it said can not connect to plymouth, maybe i should try a dodge.

---

### Post by nilarimogard on 2010-01-15
> **cecilpierce said:**
> tried two different themes on the list, says "could not start splash : no such file or directory", before it said can not connect to plymouth, maybe i should try a dodge.

Exactly this is happening to my Lucid installation too :(   I even tried a fresh Alpha 2 installation.

---

### Post by ranch hand on 2010-01-15
Did you check your /lib/plymouth directory to be sure it was all there?

---

### Post by nilarimogard on 2010-01-15
Yes, it's all there.

---

### Post by celticbhoy on 2010-01-15
> **ranch hand said:**
> Oh my, good work.  Thank you for this.

I did not look at the theme you were trying to use but can you not just take the image and replace the one in solar with it?

That worked very slick for an image that I had and used.

As each theme comes with its own script to run the elements it uses I think you will only be able to change certain things the way you suggest.

The theme I was trying to install was the space-sunrise one here :-

[http://gitorious.org/oskude-plymouth-themes/space-sunrise](http://gitorious.org/oskude-plymouth-themes/space-sunrise)

will keep plugging away to see if I can get it to go.

For those who cant get the theming to work -what hardware you on? I am on Intel graphics - dont know if that makes a difference

---

### Post by celticbhoy on 2010-01-15
> **nilarimogard said:**
> Yes, it's all there.

First if you check in the /lib/plymouth/themes/solar dir there should be 6 .png files and one called solar.plymouth.
Then check that /lib/plymouth dir contains 8 .so files, 2 sub dirs, and ubuntu-logo.png.

---

### Post by nilarimogard on 2010-01-15
That could be it, I understood it's not going to work on Nvidia and I have an Nvidia graphics card.

---

### Post by celticbhoy on 2010-01-15
> **nilarimogard said:**
> That could be it, I understood it's not going to work on Nvidia and I have an Nvidia graphics card.

You should prob have a look at the Plymouth lucid thread - more info on Nvidia outcome there.

---

### Post by celticbhoy on 2010-01-15
I think that it is safe to add that this will only work if Plymouth is already working on your hardware - It wont fix non-functioning Plymouth.

---

### Post by ranch hand on 2010-01-15
It may not work that way but I do know that I have completely changed the "solar" image three time s now and it works on all three of those installs with the new image.  The new image is not animated but the script does not do anything to define animation.  It only defines the image.

I simply edit my image to the exact size of the default image by scaling and cropping.  Hit edit>clear on the default image and copy/paste mine in and save as the default image (same file name as called in the script).

One image is a composite image of my lovely wife, another is a wallpaper from gnome-looks and the other is a lynx image from one of the forum members here (sorry I forget the name but they are very nice).

---

### Post by celticbhoy on 2010-01-15
> **ranch hand said:**
> It may not work that way but I do know that I have completely changed the "solar" image three time s now and it works on all three of those installs with the new image.  The new image is not animated but the script does not do anything to define animation.  It only defines the image.

I simply edit my image to the exact size of the default image by scaling and cropping.  Hit edit>clear on the default image and copy/paste mine in and save as the default image (same file name as called in the script).

One image is a composite image of my lovely wife, another is a wallpaper from gnome-looks and the other is a lynx image from one of the forum members here (sorry I forget the name but they are very nice).

Sorry I've been a bit slow - was tired last night. You are right the animation is handled by the .so file in the main plymouth directory. If you want to use your own background I would suggest the script theme simple with a small prograss bar. Just edit it to remove the ubuntu logo by removing all instances of the logo in script.script file and add a background.

The problem with the theme I tried to install was there was no .so file.

---

### Post by celticbhoy on 2010-01-15
This will show you how to add a background to work on any screen size :-

[http://brej.org/blog/?p=174](http://brej.org/blog/?p=174)

---

### Post by celticbhoy on 2010-01-15
forget the bit about the .so files - they are shared libs that you can include if you wish. Funny thing is that my downloaded theme works now - go figure

---

### Post by biasquez on 2010-01-15
i have a question: why if i run plymouthd and launch "/etc/init.d/plymouth start" i see two windows  with bootsplash solar running in X (kde) but if i reboot i don't see solar theme and i see error (could not start boot splash : no such file or directory)?

---

### Post by caryb on 2010-01-15
Works for me on Kubuntu 64 with the hardware below.


Cary

---

### Post by cecilpierce on 2010-01-15
tried "/etc/init.d/plymouth start", got a msg abt "service start plymouth", did that and black screen with a note on the monitor saying "out of range" and computer lockup. i have a nvidia 6200 card, 190.53 driver, 3D effects and working fine.

---

### Post by ranch hand on 2010-01-15
Ok, I am just getting started fooling around with scripts and have no idea what I am doing with the "theme" tittled "script".

I added to that file an image lxde.png.

I opened script.script and changed;
```

ImageDir=/lib/plymouth/themes/script
logo.image = Image("special://logo");
logo.sprite = Sprite(logo.image);
logo.opacity_angle = 0;

```
to include that first line as there is no Image command by default nor an image in the theme.

Rebooted and went to that OS.  Theme works!!!  Happy Happy.

However, the entire image and logo "throb".  They fade in and out.  There is a lot of stuff in that script.script that I just do not understand at all.

There is talk of "opacity" but I do not understand a bit of it or know if that is even related to the throbbing.

Does anyone have a clue for the clueless grumpy geezer?

---

### Post by BwackNinja on 2010-01-15
In the refresh_callback function, if the status is normal (which it normally is) then the opacity_angle and opacity are are calculated. opacity_angle is simply an always increasing number, that when used in "opacity = (Math.Cos(logo.opacity_angle) + 1) / 2;" will set the opacity to be moving smoothly from 0 to 1. That number is then multiplied by (1 - min_opacity) and min_opacity is added to it, so that the maximum opacity is 1, and the minimum opacity is 0, while the opacity is still set to move smoothly following a wave function.

logo.sprite.SetX and SetY are making it so that the image is drawn centered on the screen. This is why, as you found, that you need to make the image the same as your resolution for it to appear properly.

---

### Post by ranch hand on 2010-01-15
> **BwackNinja said:**
> In the refresh_callback function, if the status is normal (which it normally is) then the opacity_angle and opacity are are calculated. opacity_angle is simply an always increasing number, that when used in "opacity = (Math.Cos(logo.opacity_angle) + 1) / 2;" will set the opacity to be moving smoothly from 0 to 1. That number is then multiplied by (1 - min_opacity) and min_opacity is added to it, so that the maximum opacity is 1, and the minimum opacity is 0, while the opacity is still set to move smoothly following a wave function.

logo.sprite.SetX and SetY are making it so that the image is drawn centered on the screen. This is why, as you found, that you need to make the image the same as your resolution for it to appear properly.
Ok, I think I understand what you are saying.

Do you have any idea what I do to stop the throbbing or what is causing it?

Does the above question indicate a total lack of understanding what you said?

I really am trying to learn to be a geek speaker but it is slow going.

The image in that file was made to be 800x480 as that is the size of the image in the "solar" theme and I assumed that was the size needed by all the themes.

---

### Post by celticbhoy on 2010-01-15
> **ranch hand said:**
> Ok, I think I understand what you are saying.

Do you have any idea what I do to stop the throbbing or what is causing it?

Does the above question indicate a total lack of understanding what you said?

I really am trying to learn to be a geek speaker but it is slow going.

The image in that file was made to be 800x480 as that is the size of the image in the "solar" theme and I assumed that was the size needed by all the themes.

A bit of an ugly workaround without knowing whats going on in the script, but you could try and change the min_opacity setting to 1 from 0.3?

---

### Post by ranch hand on 2010-01-15
What about setting "status" at something other than normal?  All the opacity stuff seems to depend on that and the script for "solar" has no entry at all for most of that stuff.

Also line one of this script is;
> 
# This is an example plymouth plugin script

So I am assuming that it is like the /etc/grub.d/40_custom file where you can make your own menu entries.

Could I, in that case, just do away with the entire section about opacity?

---

### Post by celticbhoy on 2010-01-15
> **ranch hand said:**
> What about setting "status" at something other than normal?  All the opacity stuff seems to depend on that and the script for "solar" has no entry at all for most of that stuff.

Also line one of this script is;

So I am assuming that it is like the /etc/grub.d/40_custom file where you can make your own menu entries.

Could I, in that case, just do away with the entire section about opacity?

I think while we are waiting for some of the folk with large foreheads to tell us what to do, we really need to just go on trial and error. Right now I am having problems with the progress bar (although the theme I am using uses the progress settings to display the full animation). On every theme I have tried the progress bar only reaches about a third way before the desktop has loaded. I dont know if this is just my install or if the devs still have a bit of work to do on this. Any info on how the progress bars work for you will be welcomed.

---

### Post by ranch hand on 2010-01-15
Mine does the same thing on the progress bar.

I think it is time for me to do a little backing up and file editing.

---

### Post by celticbhoy on 2010-01-15
> **ranch hand said:**
> Mine does the same thing on the progress bar.

I think it is time for me to do a little backing up and file editing.

Have fun ....
:D

---

### Post by BwackNinja on 2010-01-15
> **ranch hand said:**
> Ok, I think I understand what you are saying.

Do you have any idea what I do to stop the throbbing or what is causing it?

Does the above question indicate a total lack of understanding what you said?

I really am trying to learn to be a geek speaker but it is slow going.

The image in that file was made to be 800x480 as that is the size of the image in the "solar" theme and I assumed that was the size needed by all the themes.

Kinda, yeah. What I said about the changes in the opacity is causing the throbbing, so you were definitely on the right track. Though I might've confused you a bit with the wave stuff, which was mostly just me being impressed with how I wouldn't have thought of doing it that way. Anyway, to stop it from throbbing, change "logo.sprite.SetOpacity (opacity);" to "logo.sprite.SetOpacity (1);".

I've been speaking geek for a while now, and I hope you can become fluent too. :) Once you speak a little, you can pretty much just pretend you know the rest.

---

### Post by ranch hand on 2010-01-16
Yes , I believe you.  I am a grumpy geezer.  You don't get there with out learning a thing or two about BSing your way through things.

Geek is a little tough as I really am no good with languages anyway.  On the other hand I probably speak agriculture better  than most on the forums here so I guess I can live with it.

I am on my night time OS, Stoner Edition 1.0 (9.04 respin) on an isolated drive.  I am firering up my external test platform so I can look at the file.  I had to wait for gparted to "refresh devices".  I fire it up before turning the external on thus preventing the mounting of all the partitions on that drive.

I assume that you are talking about the line with just the what you quoted in it.  That is what is there now.
> 
# This is an example plymouth plugin script

Window.SetBackgroundTopColor(0.234, 0.43, 0.705);
Window.SetBackgroundBottomColor(0.16, 0.25, 0.44);

ImageDir=/lib/plymouth/themes/script
logo.image = Image("special://logo");
logo.sprite = Sprite(logo.image);
logo.opacity_angle = 0;

fun refresh_callback ()
  {
    if (status == "normal")
      {
        logo.opacity_angle += ((2 * 3.14) / 50) * 0.5;  # 0.5 HZ
        min_opacity = 0.3;
        opacity = (Math.Cos(logo.opacity_angle) + 1) / 2;
        opacity *= 1 - min_opacity;
        opacity += min_opacity;
        logo.sprite.SetX (Window.GetWidth()  / 2 - logo.image.GetWidth()  / 2);
        logo.sprite.SetY (Window.GetHeight() / 2 - logo.image.GetHeight() / 2);
        logo.sprite.SetOpacity (opacity);
      }
    else
      {
        logo.sprite.SetX (0);
        logo.sprite.SetY (0);
        logo.sprite.SetOpacity (1);
      }
  }
  
Plymouth.SetRefreshFunction (refresh_callback);

I was thinking about some thing along the lines of having that section look like this;
> 
# This is an example plymouth plugin script

Window.SetBackgroundTopColor(0.234, 0.43, 0.705);
Window.SetBackgroundBottomColor(0.16, 0.25, 0.44);

ImageDir=/lib/plymouth/themes/script
logo.image = Image("special://logo");
logo.sprite = Sprite(logo.image);
logo.opacity_angle = 0;

All the "solar" theme has in its script is;
> 
[Plymouth Theme]
Name=Solar
Description=Space theme with violent flaring blue star
ModuleName=space-flares

[space-flares]
ImageDir=/lib/plymouth/themes/solar

and  I have replace the image on it on 3 installs and that works fine there.

I have looked at the "dialog" part of the script.script file and am not sure what all of it means but it looks like it may work better than the default setup as far as being smooth and informative so I figured leave it in there.  Besides, it could be educational and we all know that is good.

---

### Post by Ibidem on 2010-01-16
@ranch hand:
That is a tangle of functions there; every screen refresh you're changing the opacity.
It's increase one value, take a cosine, do some multiplication, and do some more math.
Apparently you need the following at minimum
fun refresh_callback ()
{
        logo.sprite.SetX (x);
        logo.sprite.SetY (y);
        logo.sprite.SetOpacity (z);
      }
where x, y, and z are numbers between 0 and 1.
My guess is that Plymouth calls refresh_callback() every screen refresh and uses the specified values to determine various things.

On another subject, you probably do speak agriculture better than anyone else...but you're not the only aggy.  (Work is better than school, but I'm starting on a B.S. in the university sense)

You'd need to know a little programming and math to appreciate what the sample theme does.

Ibidem

---

### Post by ranch hand on 2010-01-16
I am actually quite good, if rusty, at algebra.  Fun stuff that I have always loved.

Scripts are greek to me but I need to learn this stuff.  I have a coarse of study laid out, just need the time to go through it.

As far as this one is concerned I am definitely baffled right now.  I decided to just wipe the thing and then add stuff back to see what it did.  I edited the bugger down to the bone;
> 
[Plymouth Theme]
Name=Script
Description=Script plugin. not much here atm
ModuleName=script

[script]
ImageDir=/lib/plymouth/themes/script
ScriptFile=/lib/plymouth/themes/script/script.script

That is the whole thing right now.  The last line was to make sure that it was not reading the other renamed files (2) that I have in the folder (one default and the other I edited).

Fired the bugger up and would really like to know were it is getting the throb from because it is still at it.

On a more important note, just what is it you are studying and where?

---

### Post by celticbhoy on 2010-01-16
> **ranch hand said:**
> I am actually quite good, if rusty, at algebra.  Fun stuff that I have always loved.

Scripts are greek to me but I need to learn this stuff.  I have a coarse of study laid out, just need the time to go through it.

As far as this one is concerned I am definitely baffled right now.  I decided to just wipe the thing and then add stuff back to see what it did.  I edited the bugger down to the bone;

That is the whole thing right now.  The last line was to make sure that it was not reading the other renamed files (2) that I have in the folder (one default and the other I edited).

Fired the bugger up and would really like to know were it is getting the throb from because it is still at it.

On a more important note, just what is it you are studying and where?

A really daft question, but did you re-install the theme?

---

### Post by ranch hand on 2010-01-16
No.  Geeze, that might help.

Once again proving that I really am a moron.  But I am good at it.

---

### Post by celticbhoy on 2010-01-16
Everyone is good at something !!!

---

### Post by ranch hand on 2010-01-16
Yes it is good to have some skill you can depend on.

That did fix it, by the way.

Now I can get on with my day and let this OS boinc.

I will be plugging in more parts of the default script to see what they really do.  There seems to be some stuff at the end that is about closing which I think is for when you are shutting down or rebooting that is of interest to me.

I will also, sometime fool with the throbbing.  It would not be a bad thing if it didn't change quite as much and a little slower.  I have to do some studying before I mess with that.

I will even try to remember to install the theme when I do these things so my poor box knows about it.

---

### Post by vishalrao on 2010-01-16
> **caryb said:**
> Works for me on Kubuntu 64 with the hardware below.


Cary

How'd you get it to work? I have kubuntu lucid x64 and an 8800 GT...

---

### Post by Ibidem on 2010-01-16
> **ranch hand said:**
> I am actually quite good, if rusty, at algebra.  Fun stuff that I have always loved.

Scripts are greek to me but I need to learn this stuff.  I have a coarse of study laid out, just need the time to go through it.

As far as this one is concerned I am definitely baffled right now.  I decided to just wipe the thing and then add stuff back to see what it did.  I edited the bugger down to the bone;

That is the whole thing right now.  The last line was to make sure that it was not reading the other renamed files (2) that I have in the folder (one default and the other I edited).

Fired the bugger up and would really like to know were it is getting the throb from because it is still at it.

On a more important note, just what is it you are studying and where?
Agriculture, option in Crops, Horticulture, & Land Resource Management (ie, crop science) at CSU Chico.
Starting in a week (new transfer, with an AS)
I had been going for Civil Engineering, since I love math and all that, but math all week, all year is perhaps a bit much. Played with BASIC, Pascal, Python, C, & R, as well as batch and shell scripts.
I'm not using Plymouth yet; I've always removed any splash screens.
Where did the mile-long boot messages go?  I only get ~20 lines per boot, and I think they shut up the messages before fsck somehow.
But if you noticed the 
else
{
....
}
I think that is what you want to use.

Ibidem

---

### Post by ranch hand on 2010-01-16
Ibidem
Sounds like a good coarse of study to me.  So does engineering.

I know from the grub.d scripts about the brackets.  The else stuff still seems weird to me because I don't see the connection with the stuff preceding it.  Many times it seems to work the same way no matter what.

Of coarse it would probably help if I fooled around with scripts that were not in an alpha and some of them definitely experimental or incomplete themselves.

I am being optomistic about the lack of messages.  Most of us are set for a quiet splash and the lack of messages seems like a sign that they may be getting the boot sequence to work the way they want it to.

I still get several at shutdown but on most of my 7 installs I get nothing on boot up.

The reason that I have plymouth on most of those installs is because a while back I had some real bad boot problems and I tried installing plymouth.  Continued to get the same messages but the buggers would boot.  After that worked on one I installed it on every install that was a problem and they all responded.  It was not doing a thing but the presents of the file must have madee something happy enough to let the OS' boot.

I've got the bugger, I am in testing, I have an excuse to play and, perhaps, learn something.  I have everything backed up so I can revert to default if needed.

---

### Post by Ibidem on 2010-01-16
Note the if(status==normal) line.
What that means is that when "status" is equal to "normal", run everything before "else".
If "status" is not "normal", the stuff after "else" runs.
If nothing changes "status", it will run one way

See [here]("http://en.wikipedia.org/wiki/Operators_in_C_and_C%2B%2B") if you want an explanation of the operations like ==

Ibidem

---

### Post by ranch hand on 2010-01-16
Yes I wondered about changing that to something else to see what happened but I do not now what to replace it with.  I don't want it to quit on "whatever command not known" or "unexpected syntax error at"".

Thanks for the link.  I will study on that tomorrow.  My brain is pretty much done for today.

It looks like just the kind of thing I need to study.

---

### Post by Ibidem on 2010-01-16
Try this ending...
(*If you wish...*)

fun refresh_callback ()
{
        logo.sprite.SetX (0);
        logo.sprite.SetY (0);
        logo.sprite.SetOpacity (1);
      }
Plymouth.SetRefreshFunction (refresh_callback);

---

### Post by ranch hand on 2010-01-16
Heck, I'm game.  I am back on my isolated main drive right now but I will try it tomorrow when I am back on the test drive.

Thanks.

---

### Post by vishalrao on 2010-01-17
OK I got the console to work in 1024x768x24 mode and display the space-sunrise plymouth theme on my nvidia 8800GT with kubuntu 64 but the rendering is reallyyyy slowwww... :(

I had to blacklist the vga16fb module and add the vesafb module (nvidiafb doesnt seem to work for me).

I'm currently trying to get low-res low-depth ( like 800x600x8 ) to work without luck so far so that the theme renders smoothly and quickly :)

NOTE that blacklisting involves ensuring you run update-initramfs AFTER you've set everything in /etd/modules, /etc/initramfs/modules and /etc/modprobe.d/blacklist-framebuffer etc. else it wont pick up everything. I was making the mistake of changing only /etc/initramfs/modules then running update-initramfs before editing the modules/modprobe blacklists...

---

### Post by vishalrao on 2010-01-17
Update:

OK 1024x768x24 works best for me with vesafb and my nvidia 8800GT.

The slow space-sunrise animation was due to a likely bug in the theme script where the progress callback parameters are switched time <-> percent.

See: [http://www.freedesktop.org/wiki/Software/Plymouth/Scripts](http://www.freedesktop.org/wiki/Software/Plymouth/Scripts)

The script uses (tries to) the percent parameter but actually ends up looking at the time passed param so it works when you run the test.sh script but does not when you actually boot it up.

So I just assumed a 10 second boot (roughly what I get) to calculate the new percent progressed and now the animation is fast/smooth on my bootup!

I also edited the last if statement to continue rotating the ubuntu logo in case the bootup takes longer for whatever reason (fsck etc?) and it seems to work coz my bootup sometimes gets slowed down due to my SSD errors.

Now, here is a youtube video of my screen! :lolflag:

[http://www.youtube.com/watch?v=N-4xTkN1_RQ](http://www.youtube.com/watch?v=N-4xTkN1_RQ)

To fix the time/percent mixup and also ubuntu not sending the correct percent at the moment (but Im a noob so I cant say for sure) so I try to estimate a 10 sec boot:

```

p = (p * 100.0) / 10.0;

```

and to let the logo keep spinning should boot take longer, commented out the bit that checks the end percent as you see below:

```

if (p >= distroLogo.start /*&& p <= distroLogo.end*/) {

```

---

### Post by caryb on 2010-01-17
How did I get it going on Kubuntu? I just did a apt-get install Plymouth 
& that's it I didn't do any tweaking at all.


Cary

---

### Post by ranch hand on 2010-01-17
> **Ibidem said:**
> Try this ending...
(*If you wish...*)

fun refresh_callback ()
{
        logo.sprite.SetX (0);
        logo.sprite.SetY (0);
        logo.sprite.SetOpacity (1);
      }
Plymouth.SetRefreshFunction (refresh_callback);
I tried that and get nothing.  By that  I mean I get a black screen up to the login screen.

This seems to be the result of every modification I have tried to the default script except for the one with nothing but a call for the image which worked fine.

EDIT
The last thing I tried was the default script with the "normal" in the dialog section changed to "weird" (had no idea what to put there so I used "weird").  Same black screen result.

---

### Post by vishalrao on 2010-01-17
> **caryb said:**
> How did I get it going on Kubuntu? I just did a apt-get install Plymouth & that's it I didn't do any tweaking at all.

ahahaha, i, on the other hand, spent an entire sunday mucking about (including "sudo aptitude reinstall plymouth") to end up with a 10 second boot eye candy :lolflag:

---

### Post by caryb on 2010-01-17
> ahahaha, i, on the other hand, spent an entire sunday mucking about (including "sudo aptitude reinstall plymouth") to end up with a 10 second boot eye candy

It has taken me 10 mins to get this reply down as I was killing myself laughing:)

Cary

---

### Post by piratemurray on 2010-01-18
Hi everyone!

Great thread! This is really useful for me. I have a question though. Does anyone know how to change the ubuntu logo to something else? Is this a case of just replacing the logo? I'm interested to know if there is a file that points to the logo and tells Plymouth to use that since ideally I'd like to change it there.

Ta very much!

---

### Post by ranch hand on 2010-01-18
All of that is in /lib/plymouth.

The thing to do is change the logo or bar or what ever it is and use it with the origanal file name.  that way you know that everything that may call for it will find it.

This is easier than changing the scripts for every theme you ever use.

---

### Post by vade on 2010-01-18
I'd like to set script Hz to display Hz to get smoother animation. Is it possible by using script alone?

---

### Post by vishalrao on 2010-01-18
> **piratemurray said:**
> Does anyone know how to change the ubuntu logo to something else? Is this a case of just replacing the logo? I'm interested to know if there is a file that points to the logo and tells Plymouth to use that since ideally I'd like to change it there.

This link: [http://www.freedesktop.org/wiki/Software/Plymouth/Scripts](http://www.freedesktop.org/wiki/Software/Plymouth/Scripts)

Along with the space-sunrise.script file of that theme which goes to /lib/plymouth/themes/space-sunrise can serve as a great tutorial... helped me learn a lot too about loading/scaling/moving/rotating and what not :)

HTH.

For quickie you can just replace the ubuntu logo png with your own but of the same name, but the effect of the sunrise going behind the circular spinning logo is sweet.

---

### Post by piratemurray on 2010-01-19
Hi thanks for the help guys I guess what I'm interested in understanding is how

```
logo.image = Image("special://logo");
```

knows to take the ```
ubuntu-logo.png
``` from the directory ```
../
```?

Replacing this image is an awesome way to get it working but in my experience this will be overwritten every update and I'll have to do the changes again. I'm trying to create a Plymouth theme for my company's customised Ubuntu version and would like the ability for the user to switch back to a standard Ubuntu Plymouth if they so choose. If I replace the logo with our own then every other theme will be affected? Is that right?

Anyways thanks again for the help!:P

---

### Post by vishalrao on 2010-01-19
just a wild guess: perhaps its: "theme_name" + "-logo" + "extension (png)"

so its ubuntu-logo.png :D

---

### Post by piratemurray on 2010-01-19
> **vishalrao said:**
> just a wild guess: perhaps its: "theme_name" + "-logo" + "extension (png)"

so its ubuntu-logo.png :D
But then by that logic the logo for the script theme would be script-logo.png, which doesn't exist anywhere.

Thanks for your suggestion though. Perhaps this is hardcorded in the Plymouth plugin i.e. script.so?

So my other question would be: how can I edit or read this plugin? Gedit doesn't open this binary file.

---

### Post by piratemurray on 2010-01-19
> **piratemurray said:**
> But then by that logic the logo for the script theme would be script-logo.png, which doesn't exist anywhere.

Thanks for your suggestion though. Perhaps this is hardcorded in the Plymouth plugin i.e. script.so?

So my other question would be: how can I edit or read this plugin? Gedit doesn't open this binary file.
I think in answer to my own question: yes it is hardcoded into the plugin.
[URL="http://lists.freedesktop.org/archives/plymouth/2009-March/000065.html"]
http://lists.freedesktop.org/archives/plymouth/2009-March/000065.html[/URL]

But you have to compile the plugin from source and point it to the logo. I haven't tried this yet since I always have issues with compiling from source. :(

---

### Post by celticbhoy on 2010-01-19
vishalrao

can you please post your customised full space-sunrise script?

---

### Post by vishalrao on 2010-01-19
sure :)

the full script is here: [http://pastebin.ubuntu.com/359328/](http://pastebin.ubuntu.com/359328/) it is located as /lib/plymouth/themes/space-sunrise/space-sunrise.script

But there's just one added line and one modified line near the end as you can see in this diff: [http://pastebin.ubuntu.com/359327/](http://pastebin.ubuntu.com/359327/)

The "problem" for me now is, after fixing my SSD NCQ issues, my boot-from-grub-to-KDM is under 10 seconds which leaves almost no time for the theme to show up and render! haha

---

### Post by celticbhoy on 2010-01-20
> **vishalrao said:**
> sure :)

the full script is here: [http://pastebin.ubuntu.com/359328/](http://pastebin.ubuntu.com/359328/) it is located as /lib/plymouth/themes/space-sunrise/space-sunrise.script

But there's just one added line and one modified line near the end as you can see in this diff: [http://pastebin.ubuntu.com/359327/](http://pastebin.ubuntu.com/359327/)

The "problem" for me now is, after fixing my SSD NCQ issues, my boot-from-grub-to-KDM is under 10 seconds which leaves almost no time for the theme to show up and render! haha

Cheers, I found my problem, an older version of the script!

ps by the way sub 10 secs - no one likes a show off.
:)

---

### Post by celticbhoy on 2010-01-20
A quick question, now we are on plymouth, will xsplash be removed. Does it still hold the GDM background?

---

### Post by vishalrao on 2010-01-20
> **celticbhoy said:**
> Cheers, I found my problem, an older version of the script!

ps by the way sub 10 secs - no one likes a show off.
:)

are you saying there is a newer version?

oh, so THAT's why nobody like me :D

---

### Post by celticbhoy on 2010-01-20
> **vishalrao said:**
> are you saying there is a newer version?

oh, so THAT's why nobody like me :D

No - the version I had did not contain the ubuntu branding.

---

### Post by ranch hand on 2010-01-20
> **celticbhoy said:**
> A quick question, now we are on plymouth, will xsplash be removed. Does it still hold the GDM background?

I know that all on my installs are running the gdm image that is in /usr/share/images/xsplash still.

Basically I have been waiting for that guestion to answer itself because it beats me.  I have not been able to find a clue to what is going to happen to that image.  I know I have it backed up on all of mine.

---

### Post by celticbhoy on 2010-01-20
> **ranch hand said:**
> I know that all on my installs are running the gdm image that is in /usr/share/images/xsplash still.

Basically I have been waiting for that guestion to answer itself because it beats me.  I have not been able to find a clue to what is going to happen to that image.  I know I have it backed up on all of mine.

Yeah thats why I was wondering - I just changed it to match my plymouth theme, and I realized that we were still using the xsplash directory.

---

### Post by Tompalaz on 2010-01-20
I can't get the space-sunrise to work.
If got it right I'm supposed to
1) git clone git://gitorious.org/oskude-plymouth-themes/space-sunrise.git
2) run build.sh
3) move the space-sunrise folder to /lib/plymouth/themes?
I just get a black screen. Solar seems to work though.

---

### Post by celticbhoy on 2010-01-20
> **Tompalaz said:**
> I can't get the space-sunrise to work.
If got it right I'm supposed to
1) git clone git://gitorious.org/oskude-plymouth-themes/space-sunrise.git
2) run build.sh
3) move the space-sunrise folder to /lib/plymouth/themes?
I just get a black screen. Solar seems to work though.

First of, you will need to edit the space-sunrise.plymouth file in the folder /lib/plymouth/themes/space-sunrise, and change the file pointers to the /lib/plymouth folder.

I would also use the tarball from here :-

[http://gitorious.org/oskude-plymouth-themes/space-sunrise/archive-tarball/ubuntu](http://gitorious.org/oskude-plymouth-themes/space-sunrise/archive-tarball/ubuntu)

as the git version is not the ubuntu themed one.

---

### Post by Tompalaz on 2010-01-20
> **celticbhoy said:**
> First of, you will need to edit the space-sunrise.plymouth file in the folder /lib/plymouth/themes/space-sunrise, and change the file pointers to the /lib/plymouth folder.

I would also use the tarball from here :-

[http://gitorious.org/oskude-plymouth-themes/space-sunrise/archive-tarball/ubuntu](http://gitorious.org/oskude-plymouth-themes/space-sunrise/archive-tarball/ubuntu)

as the git version is not the ubuntu themed one.

Thanks, got it to work now. It's really slow/laggy at startup but running smooth and way too fast when I shutdown my computer.

---

### Post by celticbhoy on 2010-01-20
> **Tompalaz said:**
> Thanks, got it to work now. It's really slow/laggy at startup but running smooth and way too fast when I shutdown my computer.

There seems to be a problem with the whole progress thing at the mo read page 5 of this thread and you will info on changing it to work over a time scale - best to get a rough startup time first.

---

### Post by Roasted on 2010-01-20
I hope Plymouth doesn't suck. Plymouth was the reason Fedora 12 wouldn't boot up properly on my laptop. :(

---

### Post by ranch hand on 2010-01-20
> **Roasted said:**
> I hope Plymouth doesn't suck. Plymouth was the reason Fedora 12 wouldn't boot up properly on my laptop. :(
Yes, so far the bugger seems to work, kind of.  It is fun to play with silly themes for the few seconds you have before the login screen.

One of the few times I fooled with fedora it had plymouth on it and it did boot (desktop) but I really didn't like it at all.  I was not thrilled when they decided to go that route with Ubuntu.

I think It will be OK.  I sure hope so too.

---

### Post by Tompalaz on 2010-01-21
> **vishalrao said:**
> 

```

if (p >= distroLogo.start /*&& p <= distroLogo.end*/) {

```
space-sunrise is still very laggy for me.
I comment out the whole if thing.

> 
#if (p >= distroLogo.start && p <= distroLogo.end) {
#    a = remap (p, distroLogo.start, distroLogo.end, 0.5, 1);
#   b = Math.Pi * a;
#  distroLogo.sprite.SetImage (distroLogo.image.Rotate(b));
# }

Do I have to rebuild initrd after editing this script?
It is space-sunrise.script, right?
What driver are you using? 
I use the lucid 190.55 (nvidia-glx-185) with a 9400M.
edit: oh, if I use plymouth gdm won't showup and I can only see a white X.
I have to go through recovery -> resume boot and then run startx.

---

### Post by celticbhoy on 2010-01-21
> **Tompalaz said:**
> space-sunrise is still very laggy for me.
I comment out the whole if thing.


Do I have to rebuild initrd after editing this script?
It is space-sunrise.script, right?
What driver are you using? 
I use the lucid 190.55 (nvidia-glx-185) with a 9400M.

Yes after adjusting the script you have to re-install it.

---

### Post by vishalrao on 2010-01-21
to comment out i dont know if you use # or //

what you commented out will simply prevent the logo from rotating, did you also add the other line "p = (p * 100.0) / 10.0; " as the first line of the progress callback function at the end? that should adjust the boot up lag/speed (worked for me)

---

### Post by ranch hand on 2010-01-21
> **vishalrao said:**
> to comment out i dont know if you use # or //

what you commented out will simply prevent the logo from rotating, did you also add the other line "p = (p * 100.0) / 10.0; " as the first line of the progress callback function at the end? that should adjust the boot up lag/speed (worked for me)
#

---

### Post by ranch hand on 2010-01-21
I have gotten the solar theme to work in one of the 10.04 installs that it did not work in.

I reinstalled "ureadahead".  Rebooted and it was still the same but did not have the message that plymouth had been "killed".

Reinstalled plymouth and reedited the files that I had changed.  Reset the theme in terminal.

Works.


This also speeded up my boot by 10 seconds to 35.25 seconds.  This is with password login.

---

### Post by vishalrao on 2010-01-21
Doh :) the link I posted above says (in its "basics" section no less) you can use both # or // (also /*  */ works)... [http://www.freedesktop.org/wiki/Software/Plymouth/Scripts](http://www.freedesktop.org/wiki/Software/Plymouth/Scripts)

---

### Post by Tompalaz on 2010-01-22
> **vishalrao said:**
> to comment out i dont know if you use # or //

what you commented out will simply prevent the logo from rotating, did you also add the other line "p = (p * 100.0) / 10.0; " as the first line of the progress callback function at the end? that should adjust the boot up lag/speed (worked for me)
I forgot the > p = (p * 100.0) / 10.0;  line.
However I'll take a brake from plymouth for now.
Might try it later.
Will follow this thread though.

---

### Post by SevenMachines on 2010-01-23
thanks [for that vishalrao. ]("http://ubuntuforums.org/showpost.php?p=8678772&postcount=44")
on nvidia proprietary drivers i had no sign of plymouth. when i added the video resolution to grub i got plymouth, but very corrupted. With the module blacklisting and adding to the initrd i now have a very lovely solar theme!

---

### Post by MacUntu on 2010-01-29
Now that I finally got it to work with nouveau: every theme that uses a progress bar fails to represent progress properly. Do you guys have anything in the file /var/lib/plymouth/boot-duration, cause mine is empty?

The file for shutdown (/var/lib/plymouth/shutdown-duration) contains
> 0.195:-42
0.279:-50
0.309:-57
0.462:-64
0.517:-71
0.593:-78
0.631:-85
0.892:-92
0.983:-100

---

### Post by ranch hand on 2010-01-29
/lib/plymouth/boot-duration and /shutdown-duration do not exist in any of my installs.  Is this something that should be there or is it an add on?  Basically WTF?

---

### Post by MacUntu on 2010-01-29
It's **/var**/lib/plymouth/...

Maybe it gets generated when running themes with progress bars? No idea - have this on two machines.

---

### Post by ranch hand on 2010-01-29
Well, I out to be more careful.

However I still do not have these files in 4 of 5 installs that seemingly should have them.  I do have the shutdown file in the other 1 but no boot file.  The other 2 installs do not have plymouth at all as one is built from the 9.10 minimal upgraded to 10.04 with the Gnome Desktop and the other is Lubuntu 10.04.

The shutdown file I do have is similar to yours.

---

### Post by ranch hand on 2010-01-29
I have been getting the "disconnected from boot status daemon" message and had the suspicion that it had to do with plymouth (why? - beats me).  As I got booted in eventually I left it alone.

This business with the boot/shutdown files got me motivated to;
A>purge plymouth
B>delete files not removed from /lib
C>install plymouth

This was done to my main 10.04 through chroot from another 10.04 that I was doing some experimenting in.

Came back here, no message, faster boot.  Still no /var/lib/plymouth/boot-status file.

I probably should have removed the /var/lib/plymouth file but foolingaround with this OS makes me nervous.

I will try it on another install sometime later.  I really need to go cut wood right now.

---

### Post by MacUntu on 2010-01-29
Is there a way to get rid of the black screen between the splash screen and GDM/gnome-session? There is no flicker but the screen turns black as long the mouse pointer shows the busy circle.

---

### Post by MacUntu on 2010-01-31
I like it simple and minimalistic, so my theme consists of just a rotating circle of friends on a black background:

```
# circle of friends logo
cof.image = Image("cof.png");
cof.sprite = Sprite();
cof.x = Window.GetWidth() / 2 - cof.image.GetWidth() / 2;
cof.y = Window.GetHeight() / 2 - cof.image.GetHeight() / 2; 
cof.z = 1000;

progress = 0;

# rotate the cof logo
fun refresh_callback ()
{
    progress++;
    speed = 0.03;
    angle = speed * progress;
    cof.sprite.SetImage(cof.image.Rotate(angle));
    cof.sprite.SetX(cof.x);
    cof.sprite.SetY(cof.y);
    cof.sprite.SetZ(cof.z);
    cof.sprite.SetOpacity(1);
}

Plymouth.SetRefreshFunction (refresh_callback);
```

Setting an image seems to create a new sprite so I had to set the parameters every time within the callback. Seems stupid.

Here's a centered version of the logo, so the rotation center of the logo equals the center of the image: [ATTACH]145498[/ATTACH]

100x100px works fine on my 1280*768 screen.

[ATTACH]145499[/ATTACH]

---

### Post by ranch hand on 2010-01-31
That is very nice.

I am not sure about the gap between plymouth and gdm.  I like things simple too so my favorite is just using the default Ubuntu logo on a background other than black.  When using that there is no gap.  Using another theme creates the gap.  Bugs me too but I can't figure it out.

---

### Post by MacUntu on 2010-01-31
Thanks for the hint, will have a look at it later. Man, you can do a lot with the script plugin. Too bad it's just not worth the effort, since I'm seeing the splash for just five seconds or so. WE NEED SLOWER BOOT TIMES! :D

---

### Post by ranch hand on 2010-01-31
> **MacUntu said:**
> Thanks for the hint, will have a look at it later. Man, you can do a lot with the script plugin. Too bad it's just not worth the effort, since I'm seeing the splash for just five seconds or so. WE NEED SLOWER BOOT TIMES! :D
Yup, it is just too fast.  Should file a bug.

This theming is kind of like the fancier stuff in burg (grub variation).  A lot of effort for a few seconds of viewing.

---

### Post by vishalrao on 2010-01-31
@MacUntu: try using opacity functions to fade in/out (at least fading in will be easy) the logo while its rotating :P looks good already, cheers.

---

### Post by MacUntu on 2010-01-31
Sorry, I could not resist:

[[img]http://img.xrmb2.net/images/658860.png[/img]]("http://www.youtube.com/watch?v=VwPVySwkaxw")

:popcorn::D:D

---

### Post by vishalrao on 2010-01-31
haha, like the text for the video says "too bad our boot times get shorter and shorter" :lolflag:

---

### Post by rafaellaguna on 2010-02-01
Just a newbie (so silly) question: How can I define a simple background image (non animated)? I have the progress bar and every fields I need, but I can't use a "wallpaper".

Thanks in advance.

---

### Post by ranch hand on 2010-02-01
> **rafaellaguna said:**
> Just a newbie (so silly) question: How can I define a simple background image (non animated)? I have the progress bar and every fields I need, but I can't use a "wallpaper".

Thanks in advance.
Your themes are in /lib/plymouth/themes.  Pick one and follow the directions here;

[http://ubuntuforums.org/showpost.php?p=8664393&postcount=2](http://ubuntuforums.org/showpost.php?p=8664393&postcount=2)

---

### Post by MacUntu on 2010-02-01
> **rafaellaguna said:**
> Just a newbie (so silly) question: How can I define a simple background image (non animated)? I have the progress bar and every fields I need, but I can't use a "wallpaper".

Here's a theming guide:

Part 1: [http://brej.org/blog/?p=158](http://brej.org/blog/?p=158) (I skipped this one)
Part 2: [http://brej.org/blog/?p=174](http://brej.org/blog/?p=174)
Part 3: [http://brej.org/blog/?p=197](http://brej.org/blog/?p=197)
Part 4: [http://brej.org/blog/?p=238](http://brej.org/blog/?p=238)

Copy an existing theme (eg. /lib/plymouth/themes/ubuntu-logo or download the one from the guide) and change the .plymouth file to point to the right places for images and the script file. The background part goes into the .script file (see guide). If you have a wallpaper of the right size you can omit the scaling part and it boils down to:
```
wallpaper.image = Image("wallpaper.png");
wallpaper.sprite = Sprite(wallpaper.image);
wallpaper.sprite.SetZ(-10000);
```

Done.

---

### Post by rafaellaguna on 2010-02-02
Thank you very much. I'll test it now with my own design!

---

### Post by vishalrao on 2010-03-20
Following my posts here: [http://ubuntuforums.org/showpost.php?p=8997266&postcount=411](http://ubuntuforums.org/showpost.php?p=8997266&postcount=411)

I copied the default ubuntu-logo plymouth theme and added a spinning COF, stole and modified the images from the new Ubuntu branding wiki page :D

See [http://www.youtube.com/watch?v=dZuWdMsIed8](http://www.youtube.com/watch?v=dZuWdMsIed8)

Here's the simple diff to the script including a fix for typo-bug [lpbug]542458[/lpbug] :

```

--- ubuntu-logo/ubuntu-logo.script      2010-03-20 14:13:32.954553786 +0530
+++ ubuntu-logo-spin/ubuntu-logo-spin.script    2010-03-20 14:06:35.967054380 +0530
@@ -145,12 +145,25 @@ logo.y = Window.GetHeight (0) / 2 - logo
 logo.z = 1000;
 logo.sprite.SetX (logo.x);
 logo.sprite.SetY (logo.y);
-logo.sprite.SetY (logo.z);
+logo.sprite.SetZ (logo.z);
 logo.sprite.SetOpacity (1);
 
 # Spacing below the logo - in pixels
 logo_spacing = logo.height * 4;
 
+cof.image = Image ("ubuntu_logo_cof.png"); # "special://logo" is a special keyword which finds the logo image
+cof.sprite = Sprite ();
+cof.sprite.SetImage (cof.image);
+cof.width = cof.image.GetWidth ();
+cof.height = cof.image.GetHeight ();
+cof.x = logo.x + logo.width;
+cof.y = logo.y;
+cof.z = 1000;
+cof.sprite.SetX (cof.x);
+cof.sprite.SetY (cof.y);
+cof.sprite.SetZ (cof.z);
+cof.sprite.SetOpacity (1);
+
 message_notification[0].image = ImageToTintedText ("");
 message_notification[1].image = ImageToTintedText ("");
 fsck_notification.image = ImageToActionText ("");
@@ -175,6 +188,11 @@ fun draw_logo () {
     logo.sprite.SetY (logo.y);
     logo.sprite.SetZ (logo.z);
     logo.sprite.SetOpacity (1);
+    
+    cof.sprite.SetX (cof.x);
+    cof.sprite.SetY (cof.y);
+    cof.sprite.SetZ (cof.z);
+    cof.sprite.SetOpacity (1);
 }
 
 
@@ -300,6 +318,11 @@ fun animate_progress_indicator (progress
 #            opacity += 0.1;
 #        }
 #    }
+
+    rot = Math.Pi * progress;
+    cof.sprite.SetImage (cof.image.Rotate(rot));
+    
+    draw_logo();
 }

```

---

### Post by richlyn9 on 2010-03-29
> **ranch hand said:**
> I have been getting the "disconnected from boot status daemon" message and had the suspicion that it had to do with plymouth (why? - beats me).  As I got booted in eventually I left it alone.

This business with the boot/shutdown files got me motivated to;
A>purge plymouth
B>delete files not removed from /lib
C>install plymouth

This was done to my main 10.04 through chroot from another 10.04 that I was doing some experimenting in.

Came back here, no message, faster boot.  Still no /var/lib/plymouth/boot-status file.

I probably should have removed the /var/lib/plymouth file but foolingaround with this OS makes me nervous.

I will try it on another install sometime later.  I really need to go cut wood right now.


i have a similar expirence after i chrooted from alive cd to fix my karmic install.

i had a clean(without any messages) boot up before it broke but now after i choose to boot in to karmic in the burg/grub menu i get a blinking cursor on a black screen for almost 20 seconds then 2 fsck ,essages and then it says the drive is clean or something like that and then comes the karmic login screen.
i also get a few messages during shutdown
I havent tried to fix it (it does bother me though)as the install boots and works well but now i think (after reading ranchhand's post) that maybe i need to reinstall a few packages 
will that be usplash(since i am on karmic) or something else or do i need to edit a few scripts?? any ideas ?

@ranchhand:is your issue  with the messages coming up at bootup (after grub/burg and before the login) and shutdown fixed.what did you do?

---

### Post by doctordruidphd on 2010-03-29
I don't seem to have a plymouth-set-default-theme program anywhere.  Trying to execute, I get: 
```
greenman@Wolfenstein:/etc/init$ plymouth-set-default-theme
The program 'plymouth-set-default-theme' is currently not installed.  You can install it by typing:
sudo apt-get install plymouth

```

Installing and reinstalling plymouth doesn't help.
**mlocate plymouth-set-default-theme** produces nothing.

How do I get this?

PS I am trying to run it as sudo.

---

### Post by mc4man on 2010-03-29
> I don't seem to have a plymouth-set-default-theme program anywhere
The avail. ubuntu themes are now individual packages, search plymouth in synaptic and install as desired.
to change

```
sudo update-alternatives --config default.plymouth
```

---

### Post by doctordruidphd on 2010-03-29
> sudo update-alternatives --config default.plymouth

Did the job. Thank You.

---

### Post by nerdy_kid on 2010-04-07
i tried using the kubuntu theme, but i got like a 16 color display that looked like...freakyness.  Is that cause im using NVIDIA? or can i fix this somehow....thnks! :D

---

### Post by manoynmonic on 2010-04-19
```
sudo update-alternatives --config default.plymouth

```

Followed by:

```
sudo update-initramfs -u
```

Works perfectly.  These new bootsplashes are beautiful.  Too bad I never shut my machine off :P.

---

### Post by Captain Smiley Pants on 2010-04-22
> **manoynmonic said:**
> ```
sudo update-alternatives --config default.plymouth

```Followed by:

```
sudo update-initramfs -u
```Works perfectly.  These new bootsplashes are beautiful.  Too bad I never shut my machine off :P.
I've been trying to get a bootsplash going on my machine, and when I ran your commands this is what I got:

```
There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
Nothing to configure.

```It's like my machine refuses to know there is a bootsplash, and I really want one because I use a netbook and actually do have to shut it on and off regularly. :(

EDIT: I installed other plymouth bootsplashes just to see if anything could be listed. After their installation, the splashes were displayed and I picked the fade in one from the repository. After running the initramfs command and rebooting, I still had no splash. :( :(

---

### Post by Captain Smiley Pants on 2010-04-23
Bump for any ideas?

---

### Post by linuxinstalledfromhdd on 2010-04-23
Ok.. I spent maybe a half hour goofing around this..  

It is a -very- cool looking 10 second bootup screen.. 

an effect that maybe would be worth about 5 minutes trying to install it had I known..  

I really really wish someone would have just written a cool little script to install this instead because when you say something like "just copy the files" but "becareful with Naut...!" freaks out newbies just a tad and kinda reminds me of my grandpaw saying "here's that thing-ah-ma-bob.. go ahead and use it..  Just becareful though!! You'll shoot your eye out you stupid kid! ." ..  um. I spent an even longer time having to install my system just the way I want it, so naturally I feel alittle protective of it, esp when I am given kinda "vague" round about instructions on how to DO this.   Esp when fooling with my init settings at bootup..  yikes!  I'm backed up with remastersys to the hilt, but I just give up at this point..  

A gave it a go though..  LOL  :P

---

