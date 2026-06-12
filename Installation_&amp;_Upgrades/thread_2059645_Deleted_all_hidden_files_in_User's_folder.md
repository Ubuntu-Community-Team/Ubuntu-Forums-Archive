---
title: "Deleted all hidden files in User's folder"
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by Wer Bn on 2012-09-18
Hey.
I'm really sad with what just happened.
I deleted all the hidden files :(
I though it was some files from some previous installation that I made. I tough it was garbage.
But then I remembered it was the hidden files...

How can I restore them?
Ubuntu didn't even create new ones.

Now I've lost all the firefox favorites and for example the bashrc .file

Please help me.

---

### Post by dargaud on 2012-09-18
If you used *rm .**, you're as good as screwed: restore from backup. You have a backup, right ?

If you selected files in a files manager (such as konqueror, dolphin, nautilus or whatever is used in Gnome now) and pressed [delete] or used the trash icon, simply do Ctrl-Z.

Trick question: did you also delete the hidden directories such as .cups, .kde...?

---

### Post by oldos2er on 2012-09-18
> **Wer Bn said:**
> Ubuntu didn't even create new ones.


New configs should be created when you run their corresponding programs again.

Did you check ~/.local/share/Trash/ ? As dargaud said, if you used rm in terminal, they're gone.

---

### Post by Wer Bn on 2012-09-18
I did, i'm screwed...

So, can you tell what have I lost?
For as I can see I lost only the things previously said.

But Ubuntu can restore them on it's own, right?

---

### Post by iponeverything on 2012-09-18
you copy the hidden files from /etc/skel give you that new home dir feel..

---

### Post by Wer Bn on 2012-09-18
So, yeah.
Nothing I can do.
thanks

---

### Post by SlugSlug on 2012-09-18
Install backintime. The at least if there is a next time you will have a backup

---

### Post by Wer Bn on 2012-09-18
I'm not gonna be that stupid next time.
Can someone please give me the standart/default .bashrc file

Please.

---

### Post by drmrgd on 2012-09-18
Check /etc/skel/ for the default .bashrc and .profile files.

---

### Post by Wer Bn on 2012-09-18
Thank you very much :)

---

