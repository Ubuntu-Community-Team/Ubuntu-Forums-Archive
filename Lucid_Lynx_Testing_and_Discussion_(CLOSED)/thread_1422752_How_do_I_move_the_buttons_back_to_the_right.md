---
title: "How do I move the buttons back to the right??"
date: 2010-03-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by KrazyPenguin on 2010-03-05
How do I move the buttons back to the right before a strangle somebody???
thanks
:shock:

---

### Post by Nickedynick on 2010-03-05
Run gconf-editor, then find apps > metacity > general > button_layout

It'll say "maximise,minimise,close:" - just move the colon to the start of that.

---

### Post by knn on 2010-03-05
> **KrazyPenguin said:**
> How do I move the buttons back to the right before a strangle somebody???
thanks
:shock:

You don't. It's better this way, trust us, we know what's good for you.

j/k

open gconf-editor, navigate to apps/metacity/general, find button_layout, and read the instructions below. The Windows layout is ```
menu:minimize,maximize,close
```

---

### Post by KrazyPenguin on 2010-03-05
> **knn said:**
> You don't. It's better this way, trust us, we know what's good for you.

j/k

open gconf-editor, navigate to apps/metacity/general, find button_layout, and read the instructions below. The Windows layout is ```
:minimize,maximize,close
```

Ya, it seems a lot of people know what is good for me these days ;-)

yahoo as the default search , purple instead of brown, buttons on the left, wtf is next???

It is like aliens have taken over my computer :shock:

Maybe this is an early April Fools joke I don't know :shock:

Hey Devs , if your taking requests, tomorrow I would like to see Applications Menu on the Right and the Time on the Left just to really **** with my head Thanks, LOL ;-)

---

### Post by katie-xx on 2010-03-05
[SIZE=2]Screen shot there if helps

kate[/SIZE]

---

### Post by mdurham on 2010-03-05
> **nickedynick said:**
> run gconf-editor, then find apps > metacity > general > button_layout

it'll say "maximise,minimise,close:" - just move the colon to the start of that.

thanks nickedynick

---

### Post by KrazyPenguin on 2010-03-05
> **katie-xx said:**
> [SIZE=2]Screen shot there if helps

kate[/SIZE]

WOW thanks for the screenshot.

;-)

---

### Post by exploder on 2010-03-05
I think that some of the changes are so people can't say that Ubuntu is a copy of the Mac OS. I really don't mind the current layout and they may have a very good reason for trying this type of change. I am just going to leave things as they are and see what the Developers have in mind. :)

---

### Post by knn on 2010-03-05
> **exploder said:**
> I think that some of the changes are so people can't say that Ubuntu is a copy of the Mac OS. I really don't mind the current layout and they may have a very good reason for trying this type of change. I am just going to leave things as they are and see what the Developers have in mind. :)

My frustration is mostly that there's no way to customize things other than through Gnome [S]Regedit[/S] Gconf editor. Or even worse, for example to restore application titlebar icons (which was removed for stupid reasons and despite several users pointing out valid use cases why they should stays, see [https://bugs.launchpad.net/human-gtk-theme/+bug/405426](https://bugs.launchpad.net/human-gtk-theme/+bug/405426)), you have to change the theme gtkrc. Not exactly userfriendly (yes, you can change to another theme, but what if you want Human?)

---

### Post by grubdude on 2010-03-05
Me too. Living dangerously, although tough getting used to the maximize button first....Old habits die hard.;)

---

### Post by VMC on 2010-03-05
> 

open gconf-editor, navigate to apps/metacity/general, find button_layout, and read the instructions below. The Windows layout is ```
menu:minimize,maximize,close
```

This is the code for switching the max, min, and close.

 I was under the impression the OP wanted to move the button set from left to right.

---

### Post by knn on 2010-03-05
> **VMC said:**
> This is the code for switching the max, min, and close.

 I was under the impression the OP wanted to move the button set from left to right.

This is exactly what I said it was, the Windows layout, used in Ubuntu up until now.

I assumed the OP wanted to restore the previous configuration.

---

### Post by KrazyPenguin on 2010-03-05
yes , i wanted the buttons to the way they were for the last 20 years.
would really like to know the rational on this??

---

### Post by Owen.C93 on 2010-03-05
Trying something new, this is alpha testing.

---

### Post by knn on 2010-03-05
> **Owen.C93 said:**
> Trying something new, this is alpha testing.

And then before you notice it's beta, and then RC and it's still just "trying something new" until you're stuck with it.

---

### Post by Nickedynick on 2010-03-05
> **VMC said:**
> This is the code for switching the max, min, and close.

 I was under the impression the OP wanted to move the button set from left to right.

Yes, the colon dictates which side they go.

---

### Post by katie-xx on 2010-03-05
> **KrazyPenguin said:**
> yes , i wanted the buttons to the way they were for the last 20 years.
would really like to know the rational on this??
[SIZE=2]
I think these decisions are not taken lightly. From what I have seen at work small changes to an interface are deemed a major decision.
Most of our products have always had the close buttons at the bottom right of the screen. Moving to a Microsoft type layout with close buttons at top right was really stressful for us and wasnt a success. We have put them back where our clients expect to find them. This is important for control systems.
In the case of Ubuntu Im sure the decision was just as stressful and Im also sure the team would have been looking at colour wheeels and research about human machine inter actions etc etc.
Bottom line is we can configure to our own tastes. 
Maybe ..it would be a good idea to allow for some of these tweaks in the installer. 

Kate
[/SIZE]

---

### Post by grubdude on 2010-03-05
Sounds reasonable.....

---

### Post by KrazyPenguin on 2010-03-05
> **katie-xx said:**
> [SIZE=2]
I think these decisions are not taken lightly. From what I have seen at work small changes to an interface are deemed a major decision.
Most of our products have always had the close buttons at the bottom right of the screen. Moving to a Microsoft type layout with close buttons at top right was really stressful for us and wasnt a success. We have put them back where our clients expect to find them. This is important for control systems.
In the case of Ubuntu Im sure the decision was just as stressful and Im also sure the team would have been looking at colour wheeels and research about human machine inter actions etc etc.
Bottom line is we can configure to our own tastes. 
Maybe ..it would be a good idea to allow for some of these tweaks in the installer. 

Kate
[/SIZE]

I suggest you google "muscle memory".
It means that you can do physical things automatically without conscientiously thinking about it.
A good example would be driving a car.
What do you think would happen if we reversed the brake and accelerator pedal???? 
It would be a disaster and thousands of people would probably die on the first day.  Not because we don't know they are reversed, but due to muscle memory.  You don't have to think where the brake pedal is, and in an emergency stop, you just step on it hard to stop.

Now my muscle memory, which I have no control over, has my mouse automatically move to the right side of screen when I want to close a window in Ubuntu.  Eventually I will get used to the left side, after training my muscles.  At this point there will be no thinking, it will happen automatically, but why do we need the extra muscles memory training????
Is there a purpose??
thanks

---

### Post by VMC on 2010-03-05
> **knn said:**
> This is exactly what I said it was, the Windows layout, used in Ubuntu up until now.

I assumed the OP wanted to restore the previous configuration.

I misread the colon part of the statement, from "/apps/metacity/general/button_layout":
> Arrangement of buttons on the titlebar. The value should be a string, such as "menu:minimize,maximize,spacer,close"; _the colon separates the left corner of the window from the right corner_, and the button names are comma-separated. Duplicate buttons are not allowed. Unknown button names are silently ignored so that buttons can be added in future metacity versions without breaking older versions. A special spacer tag can be used to insert some space between two adjacent buttons. 

---

### Post by Robertjm on 2010-03-05
Kind of interesting.

If you add the colon to the beginning, but forget to remove the colon at the end, it treats the second colon as part of the last button name, turning it to "close:" and ignores it as invalid, only showing the first two names.

---

### Post by gibbylinks on 2010-03-06
Cheers, that's what I love about this OS, it's just so easy to change stuff !! (and break it lol !):P

---

### Post by knn on 2010-03-06
> **gibbylinks said:**
> Cheers, that's what I love about this OS, it's just so easy to change stuff !! (and break it lol !):P

Easy? You probably haven't seen KDE before.

---

### Post by Atermoon on 2010-03-06
> **knn said:**
> Easy? You probably haven't seen KDE before.
Yeah, breaking stuff in KDE is easier :lolflag:

---

### Post by Uncle Spellbinder on 2010-03-06
Weird. Went to sleep last night, buttons were on the right. Woke up this morning, booted Lucid and buttons are now on the left.

:-k

---

### Post by VMC on 2010-03-06
> **Uncle Spellbinder said:**
> Weird. Went to sleep last night, buttons were on the right. Woke up this morning, booted Lucid and buttons are now on the left.

:-k

Did you sleep on your Left side or Right side :)

---

### Post by Uncle Spellbinder on 2010-03-06
> **VMC said:**
> Did you sleep on your Left side or Right side :)
Left. I guess that explains it!


:lol:

---

### Post by moore.bryan on 2010-03-06
Has anyone else noticed after the latest round of updates, the minimize, maximize, and close icons are placed on the left-side of the window regardless of which theme your using?

Just checking to see if it's just me...

---

### Post by howefield on 2010-03-06
No it's not just you, it is a deliberate change to the UI. Isn't it marvellous ? :)

If you want to change it, see this thread.

[http://ubuntuforums.org/showthread.php?t=1422752](http://ubuntuforums.org/showthread.php?t=1422752)

---

### Post by Keyper7 on 2010-03-06
I don't want to be rude, but you could at least **try** to search for similar threads before posting yours.

There are some active ones in the very first page.

---

### Post by moore.bryan on 2010-03-06
> **howefield said:**
> No it's not just you, it is a deliberate change to the UI. Isn't it marvellous ? :)

If you want to change it, see this thread.

[http://ubuntuforums.org/showthread.php?t=1422752](http://ubuntuforums.org/showthread.php?t=1422752)
Thanks, howefield, I didn't know we were changing-up the UI...

> **Keyper7 said:**
> I don't want to be rude, but you could at least **try** to search for similar threads before posting yours.

There are some active ones in the very first page.
That was *very* rude, Keyper7... ;-)

I did a search, but as I wasn't even sure what keywords to look for, I failed to find any...

---

### Post by Keyper7 on 2010-03-06
> **moore.bryan said:**
> I did a search, but as I wasn't even sure what keywords to look for, I failed to find any...

The title "How do I move the buttons back to the right??", in the very first page, is not exactly the kind of title that makes you think "oh, this probably has absolutely nothing to do with my issue of buttons on the right side, so I won't even click on it".

Furthermore, if you search for "window buttons", four out of the five first occurrences relate to your issue.

The combinations "window icons", "maximize minimize close", "icons left side" and "buttons left side" are also good enough, and are all quite straightforward.

Finally, most of the above combinations also work if you use them on Google and prefix them with "ubuntu".

---

### Post by Technoviking on 2010-03-06
Lets keep the discussion civil. I'm sure it was an honest mistake. I will merge the threads.

Cheers,
T-V

---

### Post by uRock on 2010-03-06
I went through the steps to change my buttons back to being on the right and it didn't work. Is there something else I am supposed to do?

---

### Post by VMC on 2010-03-07
> **iRock said:**
> I went through the steps to change my buttons back to being on the right and it didn't work. Is there something else I am supposed to do?

No, unless you missed something. You did type return after changing. Look at "**/apps/metacity/general/button_layout**", and make sure it is like this: "**:minimize,maximize,close**"

---

### Post by uRock on 2010-03-07
> **VMC said:**
> No, unless you missed something. You did type return after changing. Look at "**/apps/metacity/general/button_layout**", and make sure it is like this: "**:minimize,maximize,close**"

Yep, tried it, just like that. I am thinking there is something different that has to be changed with the Netbook Edition.

---

### Post by KrazyPenguin on 2010-03-07
> **Keyper7 said:**
> I don't want to be rude, but you could at least **try** to search for similar threads before posting yours.

There are some active ones in the very first page.

Rude post.
The reason I started this thread wasn't to question why the buttons were moved, or to comment on it, but rather to determine how to move the buttons back without having to read through an entire thread.  It is probably something many people wanted to know, including myself, and should have been stickied in the first place. Thanks.

---

### Post by forcecore on 2010-03-07
Do not tell me that these buttons will stay, no one likes them, i showed lastest daily to some people and result was that they hated it and i too. Who wants these buttons on left then change there but DEFAULT it must be on RIGHT side.

---

### Post by basilwatson on 2010-03-07
> **iRock said:**
> Yep, tried it, just like that. I am thinking there is something different that has to be changed with the Netbook Edition.

Me to 

I moved the semi colon and it wouldn't change 

I am using the alpha 3 full edition on a msi wind 100

any thought on how to change the button position?

Stephen

---

### Post by KrazyPenguin on 2010-03-07
> **basilwatson said:**
> Me to 

I moved the semi colon and it wouldn't change 

I am using the alpha 3 full edition on a msi wind 100

any thought on how to change the button position?

Stephen

Did you try rebooting? i had to reboot in order for it to change on my notebook.

---

### Post by Robin Nixon on 2010-03-07
> **basilwatson said:**
> Me to 

I moved the **semi colon** and it wouldn't change 

I am using the alpha 3 full edition on a msi wind 100

any thought on how to change the button position?

Stephen

I think it should be a colon, not a semi colon.

---

### Post by silentShab on 2010-03-07
> **basilwatson said:**
> Me to 

I moved the semi colon and it wouldn't change 

I am using the alpha 3 full edition on a msi wind 100

any thought on how to change the button position?

Stephen

I had the same problem, but it worked when I ran gconf-editor with normal user permissions (instead of using sudo).  I didn't even have to reboot, it updated instantly.

---

### Post by zykotick9 on 2010-03-07
Rather then running gconf-editor you can also make the change from a terminal using:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":maximize,minimize,close"
```

---

### Post by VMC on 2010-03-07
> **zykotick9 said:**
> Rather then running gconf-editor you can also make the change from a terminal using:

```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":maximize,minimize,close"
```

Hey, this is helpful, thanks.

---

### Post by stardustdk on 2010-03-14
Hey all.

I know that 10.04 isn't finished yet, i am testing it anyway, but get annoyed by the buttons on the left side.

Is the an easy way to put the buttons to the right side on whatever window, i choose top open?

Best regards

Stardustdk

---

### Post by dcstar on 2010-03-14
> **stardustdk said:**
> Hey all.

I know that 10.04 isn't finished yet, i am testing it anyway, but get annoyed by the buttons on the left side.

Is the an easy way to put the buttons to the right side on whatever window, i choose top open?

Best regards

Stardustdk

Yep, the answer is where is should be, in the 10.04 Development forum where **all** 10.04 pre-release issues are.

---

### Post by Prometheus7 on 2010-03-14
Not sure if this is the easiest way, but the best way is to just use gconf-editor or gconf-tools...

press alt+f2, run "gksu gconf-editor" (type in your password)
browse to apps/metacity/general (in the left panel)
double click on "button_layout" (in the right panel)
change the text to "menu:minimize,maximize,close"
read the "key documentation" below to understand what you are doing
voila!

---

### Post by uRock on 2010-03-14
[HowTo put the buttons where they belong.]("http://ubuntuforums.org/showthread.php?p=8963718")

---

### Post by richs-lxh on 2010-03-14
EDIT: too late

---

### Post by uRock on 2010-03-14
Being it is such an issue, I put it in me siggy.

---

### Post by colobix on 2010-03-14
It is quite annoying with these buttons there.
They should really come up with an easier way to move the buttons before they release it.

---

### Post by uRock on 2010-03-14
[Vote about it here.]("http://ubuntuforums.org/showthread.php?t=1422422")

---

### Post by scouser73 on 2010-03-14
If you install [[COLOR="Red"]**Ubuntu Tweak**[/COLOR]]("http://ubuntu-tweak.com/"), there is an option to position the window buttons on the right, or on the left.

Once you've installed Ubuntu Tweak, open it up and go to Window Manager Settings and make your selection.

[[IMG]http://img48.imageshack.us/img48/47/windowstools.th.png[/IMG]](http://img48.imageshack.us/my.php?image=windowstools.png)

---

### Post by stardustdk on 2010-03-15
Thank you all for your replies :)

Best regards

Stardustdk

---

### Post by nilarimogard on 2010-03-15
For just setting the buttons on the right, the gconf command is enough. But this is the most easy way to customize the buttons order: [mwbuttons]("http://www.webupd8.org/2010/03/mwbuttons-complete-gui-for-customizing.html")

---

### Post by 23meg on 2010-03-15
Threads on the same topic merged.

---

