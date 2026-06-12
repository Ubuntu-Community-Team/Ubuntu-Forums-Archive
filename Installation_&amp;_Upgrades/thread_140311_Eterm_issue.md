---
title: "Eterm issue"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by paxmaster on 2006-03-05
when I try to use this command 
Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x35+13+495 -f lightgrey

I can't type anythink in Eterm

---

### Post by bluevoodoo1 on 2006-03-05
Hmmm.... you can't type anything in??? Out of curiosity, what color is your wallpaper? And also what resolution is your screen at? Can you open Eterm with "Eterm" and see if you can type anything in? You did click on the Eterm window to make the cursor solid right? Because if you don't click on the "window" you can't type anything in. 

> Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x35+13+495 -f lightgrey
(that command looks familiar :mrgreen: )

---

### Post by paxmaster on 2006-03-06
I am using fluxbox and yeah I was looking at your guide on blackbox 
let me show you what happen when i type in a command line so you will have better understanding 
 Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --geometry 79x35+13+495 --font-fx none -f lightgrey
Eterm:  Warning:  Window Manager does not support MWM hints.  Bypassing window manager control for borderless window.

the theme that I am using is NYZ that came with fluxbox 

Thanks

---

### Post by bluevoodoo1 on 2006-03-06
Ok. I was only asking about themes to see if the lightgrey text was potentially the same as a lightgrey background. Nevermind, it was silly!... anyway...

Hmm, seems like fluxbox doesn't like all those extras, especially the borderless window. 

If you type... 
```
Eterm -0 --trans --scrollbar=off --buttonbar 0
```

What happens? There will be a title bar, but the background should still be transparent (if you're using Esetroot to set your background). Does the text work?

---

### Post by paxmaster on 2006-03-06
this command works Eterm -0 --trans --scrollbar=off --buttonbar 0
and it don't give error but as you said there is a title bar 

the command that I set my background is fbsetroot

---

### Post by bluevoodoo1 on 2006-03-06
Ok, the option -x will allow Eterm to read from the user.cfg file. It should be in your .Eterm/themes/Eterm folder. From there you can edit what you like so that you can type Eterm -x and get all the goodies rather than a long list of things. Within this config file there is an option for borderless, make sure it says "borderless 0" then put the -x command in your Eterm command with all the other options, OR fix the cfg file to your liking so all you have to do is type Eterm -x... so either

edit your cfg and add borderless 0 to the file...
```
Eterm -x -0 --trans --scrollbar=off --buttonbar 0
```

or

edit the entire cfg to your liking and type...
```
Eterm -x
```

I do not see an option for transparency in the cfg file or geometry, so if you want those, -0, --trans and --geometry might have to stay in the long command.

For me, I have only modified the borderless 0 option in the cfg and I use a long command to open it. I have it on my menu so that I do not have to type it, here's mine...

```
Eterm -x -0 --trans --scrollbar=off --buttonbar 0 --save-lines 999 --geometry 85x33+13+475 -f lightgrey -F "-bitstream-bitstream vera sans mono-medium-r-normal-*-11-*-*-*-m-*-iso8859-1"
```

Also, I'm not very familiar with Fluxbox (just Blackbox) so I'm not sure if the borderless feature will even work. I hope it does though!

---

### Post by anatole on 2006-03-12
i have the same problem too. it happens only in dapper, not in breezy, both with openbox and metacity. (that's the two i tried.) setting the 'borderless' value to 0 and starting with -x did not help either.

---

### Post by b0rsten on 2006-03-15
having the same problem here :(

>  Window Manager does not support MWM hints.  Bypassing window manager control for borderless window.

---

### Post by saax on 2006-06-04
Hello

I would like to use this theme every time i open Eterm ,please tell me how to set up 

Theme > Eterm --trans -g 75x25 -f white -F '-*-lucidatypewriter-medium-r-normal-sans-15-*-*-*-*-*-*-*' -O --tint=#ffffff --shade 0 --borderless --scrollbar-popup --scrollbar-floating --scrollbar no --double-buffer -a "toggles buttonbar false"

---

