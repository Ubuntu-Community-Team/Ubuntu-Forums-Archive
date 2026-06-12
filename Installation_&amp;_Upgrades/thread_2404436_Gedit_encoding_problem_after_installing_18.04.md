---
title: "Gedit encoding problem after installing 18.04"
date: 2018-10-24
forum: Installation &amp; Upgrades
---

### Post by vampyra666 on 2018-10-24
Hello people, I have a problem that drives me crazy after performing a clean install of the 18.04 LTS.... I used to run 14.04 with no problems, but I wasn't able to use certain applications unless I upgraded, so here I am, full of problems.

I use greek characters as a native greek speaker and - for the love of me- cannot manage to set the permanent encoding to Greek. Not even a temporary one. I tried opening a file and changing the encoding from the menu below, but nothing happened. I tried moving the Greek-1253 up the top, nothing. The most frustrating is that I cannot even start creating a gedit document with greek characters, I just haven't managed to type in greek at all. All i get is small boxes instead of letters. Any idea why this is happening and what I can do to solve it? It only happens in Gedit... Thanks in advance. I'm attaching a screenshot .

---

### Post by dino99 on 2018-10-24
Is greek  set system wide inside System Settings menu ?
Check if the required greek font(s) is/are well installed first.

A relative discussion: [https://askubuntu.com/questions/741806/how-can-i-change-language-but-only-for-the-terminal](https://askubuntu.com/questions/741806/how-can-i-change-language-but-only-for-the-terminal)

That does not exlude a possible bug indeed.

---

### Post by vampyra666 on 2018-10-24
I've tried setting the Greek language wide side and nothing changed. The problem is ONLY in Gedit, everything else works fine.

---

### Post by dino99 on 2018-10-24
From the gedit top bar, click on the hamberger icon, then on tool, there is a language setting.

---

### Post by Impavidus on 2018-10-24
Using something like Windows-1253 is old-fashioned nowadays. We now have a single encoding for all scripts, known as UTF-8 (ignoring some details here). Those old 8-bit encodings constantly cause compatibility issues and should be avoided. Of course, there are still many files in those old encodings around.

Your problem might be that gedit is set to use a font that doesn't support greek characters.

---

### Post by vampyra666 on 2018-10-24
> **Impavidus said:**
> Your problem might be that gedit is set to use a font that doesn't support greek characters.

Yeap. That was it.... My husband forgot to mention he changed that! :D
Thank you!!!

---

