---
title: "Cursor won't change properly anymore"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by Exüberance on 2010-05-14
I've been using a version of the Vista cursor that I made green since I got Ubuntu 9.10. Unfortunately, when I switched to Ubuntu 10.4, it... broke. The green cursor shows up in firefox and the busy cursor works sometimes, but most of the time it just used the normal DMZ-White cursor.

What changed? How can I fix this?

I only made one cursor size since that's all I would need. Do cursors need to support multiple sizes to work now or something?

---

### Post by conradin on 2010-05-14
how did you change the cursor colour?

---

### Post by Exüberance on 2010-05-17
I just made a bunch of cursor using xcursorgen and images of the default Vista cursor I turned green in GIMP, then named the cursors to match the names used by other built-in cursor set and put them in their own directory.

It worked perfectly in Ubuntu 9.10, but when I copied the files over, and set the cursor it didn't work properly anymore. I checked the symbolic links to make sure they worked and added a few more in, but it still only uses my cursor in certain places and uses the normal default cursor everywhere else.

EDIT: It's not just my custom cursor, even the built-in ones fail. All of them. No matter what cursor I choose, it always uses the default DMZ_White cursors for almost everything. When running firefox, the correct pointer shows when the mouse is there, and it always uses the correct pointer for text selection, but everything else fails and uses DMZ_White instead of what I tell it to use.

---

### Post by Exüberance on 2010-05-17
AHA! I fixed it! This "solution" will probably change the cursor for ALL users, but oh well.

To fix this and make Ubuntu use the right cursors, go to /etc/alternatives and change the symbolic link so that it links to the theme file for YOUR cursor instead of the DMZ-White one.

To do this:
```

sudo rm /etc/alternatives/x-cursor-theme
sudo ln /usr/share/icons/**Your Cursor Theme Name Here**/cursors/cursor.theme

```If the cursor you're using doesn't have a cursor.theme file, create one and put the following text in it
```

[Icon Theme]
Inherits=**Your Cursor Theme Name Here**

```(note it goes in the /usr/share/icons/[THEME_NAME_HERE] folder, NOT the /usr/share/icons/[THEME_NAME_HERE]/cursors folder)

Or just use [this](http://launchpadlibrarian.net/48628343/change-cursor) shell script (just pass the name of the cursor theme as an argument and it will fix the link and create a theme file for you if it does not exist)

I've filed a bug report for this [here]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/581972").

---

### Post by NeverHide on 2010-05-19
help!!! I used your suggestion to fix this problem and now for some reason i've lost th window border from all windows :S
P.S. problem with cursor not changing is still the same but now i get the default black cursor instead of the white


edit:i sorted out the problem with the window borders....problem with the cursor is still there :(

---

### Post by The Knight on 2010-05-25
Hi folks,

Been having this accursed cursor problem for ages in 9.10, upgraded to 10.04 in the hopes of a fix... :(

BUT! Have now fixed it! Now, I'm pretty damn new to Ubuntu and I don't know a whole lot about detailed complex PC stuff, so this may not be the best or most streamlined way of doing things - but what I did's this. 

When you download a cursor, you *should* be able to just drop the tarball into the Appearance window. But that don't quite work by itself, and you get the problem the OP's described. So I figured I'd extract out the cursor's folder, and move it myself into the /usr/share/icons/ folder, where I know cursors should go (why it isn't called, say, /use/share/cursors/ is beyond me, but hey).

Ran into first problem: not allowed to move things into system folders. Luckily, terminal is at hand. Ran (for example):

```
sudo mv /home/tom/Downloads/Obsidian /usr/share/icons/
```

And that was fine and dandy. Clicked the mouse theme I wanted in the Appearance settings box - still nothing. Then what the guy up here said made me think, so I looked in that cursor folder. And I saw that there's a file in the first directory of that cursor folder called index.theme. And that didn't seem right to me. So I renamed it to cursor.theme (again, had to use terminal; actually, what I did is make a copy of the index.theme called cursor.theme):

```
sudo cp /usr/share/icons/Obsidian/index.theme /usr/share/icons/Obsidian/cursor.theme
```

And it works like a dream. Did this to all my cursor folders and now I can pick and choose 'em from the Appearance window and it shifts automatically. Aww yeah.

EDIT: for an utterly inexplicable reason, changing to advanced Desktop effects screwed it up. There is still a fix, though: 

```
sudo gedit /usr/share/icons/index.theme
```

And change the inherits= value to the name of the folder that contains your desired cursor in /usr/share/icons.

---

### Post by tdmsbn on 2010-05-25
Thanks you so much, I've been looking around for a fix to this minor annoyance to this issue sense Ubuntu 9.04. I love this community.

---

### Post by musdem on 2010-05-29
interestingly enough im having the exact same problem as [NeverHide]("http://ubuntuforums.org/member.php?u=1078254") the cursor has changed to the black theme. any ideas on how to fix this?

---

### Post by n00b.link on 2010-05-30
thanks guys, this was very helpful.. now i have the cursor back

---

