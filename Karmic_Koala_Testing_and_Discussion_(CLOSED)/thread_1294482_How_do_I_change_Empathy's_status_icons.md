---
title: "How do I change Empathy's status icons?"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cwk on 2009-10-18
I've been using Empathy instead of Pidgin since I upgraded to Karmic a while back, and there are a couple things that really bug me about it.

First is the fact that I can't link multiple accounts to one contact, which Google tells me is a known problem that is non-trivial to fix, so I guess I have to live with it.

Second -- and I feel like I should have some control over this -- is its butt-ugly status icons. They look completely out of sync with the rest of the icons in my notification tray, and don't change at all when I change the system icon theme. 

Is there an easy way to change out Empathy's icon theme? Can I make it match the rest of Humanity somehow?

I know it's a pretty minor cosmetic issue, but it irritates me every time I have to look at my panel.

---

### Post by falconindy on 2009-10-18
Are you talking about, for example, the ugly red triangles for 'away' status? Those should be replaced with updates to Empathy. Latest releases use status icons similar to that of Pidgin.

---

### Post by cwk on 2009-10-18
> **falconindy said:**
> Are you talking about, for example, the ugly red triangles for 'away' status? Those should be replaced with updates to Empathy. Latest releases use status icons similar to that of Pidgin.

Yeah, those triangles, this monstrosity [IMG]http://img.photobucket.com/albums/v244/CeneK/Screenshot-15.png[/IMG], the gray box. They're all pretty bad.

I'm using v. 2.28.0.1. Is that not the latest?

---

### Post by falconindy on 2009-10-18
I'm not on Karmic atm, but it looks like the version you have is the latest available.

I felt that the new icons were certainly an improvement over the old, but still needed a little more refinement. Definitely not the only part of Empathy that needs it...

---

### Post by lessthanjake on 2009-10-20
You need to create these files, I just copied the image files from Pidgin.```
$> tree $HOME/.icons/hicolor/
$HOME/.icons/hicolor/
|-- 16x16
|   `-- status
|       |-- empathy-available.png
|       |-- empathy-away.png
|       |-- empathy-busy.png
|       |-- empathy-extended-away.png
|       `-- empathy-offline.png
|-- 22x22
|   `-- status
|       |-- empathy-available.png
|       |-- empathy-away.png
|       |-- empathy-busy.png
|       |-- empathy-extended-away.png
|       `-- empathy-offline.png
|-- 24x24
|   `-- status
|       |-- empathy-available.png
|       |-- empathy-away.png
|       |-- empathy-busy.png
|       |-- empathy-extended-away.png
|       `-- empathy-offline.png
|-- 32x32
|   `-- status
|       |-- empathy-available.png
|       |-- empathy-away.png
|       |-- empathy-busy.png
|       |-- empathy-extended-away.png
|       `-- empathy-offline.png
`-- 48x48
    `-- status
        |-- empathy-available.png
        |-- empathy-away.png
        |-- empathy-busy.png
        |-- empathy-extended-away.png
        `-- empathy-offline.png

```

---

