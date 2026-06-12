---
title: "Jaunty shutdown window doesn't open in foreground"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lotus49 on 2009-04-12
I am running 9.04 beta and I have noticed that when I press my power button or click on "Shut Down" from the Gnome menu, the shut down window opens behind whichever window has the focus (but in front of any other open windows).  It only appears in the foreground if no application has the focus.

This is a decidedly annoying feature as I then have to click on the window selector to bring it to the foreground.

Does anyone know whether this is a bug or a feature (ie something I can configure it to stop doing)?

---

### Post by PacSci on 2009-04-12
I don't know much about Jaunty, but you might be able to do something like this with DevilsPie. To install it, run the command:

```
sudo apt-get install devilspie
```

Then, create a folder in your home directory named ".devilspie", and create a file named "shutdown.ds", in which you should write:

```

(if
    (is window_name "the_title_of_the_shutdown_window")
    (above)
)

```

Obviously, you'll need to replace "the_title_of_the_shutdown_window" with the actual title of the shutdown window. (I don't have access to that information.) Log out, then log back in. It should apply.

No guarantees that this will work, but it should. If you want to modify the script, check out [http://foosel.org/linux/devilspie]("http://foosel.org/linux/devilspie").

---

### Post by lotus49 on 2009-04-13
Thanks very much for the suggestion.

While I don't think I should have to resort to using another application just to get this window to appear in the foreground, your suggestion was easy to apply and works perfectly.

EDIT

I was mistaken, it didn't work unfortunately.  I have written a script based on yours (you missed off the brackets around window_name) which seems to be able to perform other actions such as minimising, but the (above) directive doesn't seem to do anything.  I am investigating.

SECOND EDIT

I have now fixed this but the solution looks rather odd now but works.  For some reason that I cannot understand the (below) directive achieves what I was after ie bringing the window into the foreground.  This is clearly backwards, but it works so I don't really care.  Devil's Pie is a really nifty application so thanks for the introduction to it.

This is what my script looks like:

```
(if 
    (is (window_name) "Shut Down the Computer") 
    (below)
)
```

---

