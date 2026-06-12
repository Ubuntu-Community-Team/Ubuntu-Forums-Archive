---
title: "Handbrake in Karmic doesnt run"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ninjapirate89 on 2009-09-29
I ran ghb in the terminal and it spit this at me:
```

(ghb:10934): Gtk-WARNING **: Failed to set property GtkToolbar.icon-size to GTK_ICON_SIZE_DND: Could not parse integer `GTK_ICON_SIZE_DND'

```

---

### Post by ninjapirate89 on 2009-09-30
bump

---

### Post by artjermyn on 2009-10-01
I'm having the same problem.  karmic beta.

---

### Post by ninjapirate89 on 2009-10-01
> **artjermyn said:**
> I'm having the same problem.  karmic beta.

I ended up just reinstalling Jaunty until Karmic is done.

---

### Post by unique on 2009-10-01
Same here... Then I found Arista Transcoder... This thing Rocks!

---

### Post by ninjapirate89 on 2009-10-01
> **unique said:**
> Same here... Then I found Arista Transcoder... This thing Rocks!

That looks nice, but it looks to be less configurable than Handbrake. 

[http://www.programmer-art.org/projects/arista-transcoder]("http://www.programmer-art.org/projects/arista-transcoder")

---

### Post by amauk on 2009-10-01
handbrake isn't in the repos, and the project download page only has 9.04
I assume this is either a PPA or self-compile?

---

### Post by steev182 on 2009-10-01
I'm having the same issue and it's the .deb from handbrake's site for me.

---

### Post by amauk on 2009-10-01
installing the pre-built 9.04 .deb on 9.10 will cause issues (it'll be linked to wrong versions of libraries)

---

### Post by artjermyn on 2009-10-01
Ahhh, just found this link:
[http://handbrake.fr/snapshot.php]("http://handbrake.fr/snapshot.php")

This is the new snapshot.  Download the deb and install.  Working good for me.

---

### Post by ninjapirate89 on 2009-10-01
> **amauk said:**
> handbrake isn't in the repos, and the project download page only has 9.04
I assume this is either a PPA or self-compile?

PPAs can be added for both Handbrake and for Arista. I'm installing Arista on Jaunty to check it out right now.

---

### Post by ninjapirate89 on 2009-10-01
Just got done installing and looking over Arista and I was right. It is less configurable than Handbrake but if all you need are basic presets for specific devices then it should work fine for your needs (I haven't actually tried it to see how well it works because I am using Handbrake at the moment).

---

### Post by crjackson on 2009-10-01
> **unique said:**
> Same here... Then I found Arista Transcoder... This thing Rocks!

it does look nice but how do you tell it to encode the file?  I can't find the start button.

---

### Post by ninjapirate89 on 2009-10-01
> **crjackson said:**
> it does look nice but how do you tell it to encode the file?  I can't find the start button.

I think you just set your preferences on the right then click the plus button on the top left to add it to the queue.

---

### Post by crjackson on 2009-10-01
> **ninjapirate89 said:**
> I think you just set your preferences on the right then click the plus button on the top left to add it to the queue.

Yeah, did all that.  I figure your supposed to click the pause button next to the + button.  But it stays grayed out and not selectable.  I must be missing something.

---

### Post by ninjapirate89 on 2009-10-01
> **crjackson said:**
> Yeah, did all that.  I figure your supposed to click the pause button next to the + button.  But it stays grayed out and not selectable.  I must be missing something.

Here is exactly how I did it:
1. Under settings select your source.
2. Choose a device to transcode for. I chose Computer.
3. Click the add button on the top left.
4. Choose a save location and a filename. I left the default name and saved to desktop. Click Save on the bottom right.
5. It starts automatically after this.

---

