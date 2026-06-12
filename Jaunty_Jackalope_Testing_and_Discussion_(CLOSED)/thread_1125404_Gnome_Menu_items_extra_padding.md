---
title: "Gnome Menu items extra padding"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by marcb on 2009-04-14
Hello,

I realized that Gnome Menu items have extra padding that, in my opinion, is unnecessary (specially for menus with fewer items). This changed between Alpha-1 and Alpha-6 (don't know where exactly, I just browsed some screenshot tours on the Internet).

Is there any way to revert back to the old behavior? Is this a Gnome change or an Ubuntu change?

I am posting some screenshots to better explain this. The one without red rectangles is for Intrepid, the other for Jaunty Beta (it is the same in Alpha-6)

Thank you very much!!!

---

### Post by sonicb00m on 2009-04-14
Never noticed that! Yes, the padding seems unnecessary. No idea how to fix it though :D

---

### Post by marcb on 2009-04-14
I have just used the official Gnome 2.26 VM image to test it and I can confirm that the extra padding is there, so it is not an Ubuntu setting.

Does anyone know if this is a bug or a "feature", to open a bug report?

Thanks!

---

### Post by chrisccoulson on 2009-04-14
I suspect it was this change in gtk:

> 2008-11-01  Matthias Clasen  <mclasen@redhat.com>

	Bug 322934 – Replace menu's proxy icons with empty space hiding icons

	* gtk/gtkmenu.c (gtk_menu_size_request): Use consistent padding
	regardless of imagees or checks being in the menu. Also add
	padding on the right edge.
	Proposal by Luca Ferretti, patch by Jon McCann

---

### Post by nelsoniv on 2009-04-14
Has anyone else noticed that when an application laucher icon on the Gnome panel is clicked there's no longer the visual echo around the icon that used to follow, indicating the app was opening?

It was visual candy fluff I know but I used to find it strangely reassuring.

---

### Post by chrisccoulson on 2009-04-14
> **nelsoniv said:**
> Has anyone else noticed that when an application laucher icon on the Gnome panel is clicked there's no longer the visual echo around the icon that used to follow, indicating the app was opening?

It was visual candy fluff I know but I used to find it strangely reassuring.

That's still working ok for me

---

### Post by nelsoniv on 2009-04-14
Just re-booted and the visual pop is back again!:popcorn:

---

### Post by marcb on 2009-04-14
> **chrisccoulson said:**
> I suspect it was this change in gtk:

Sooo it looks like it is a "feature" (annoying for me, though, it feels very weird in some situations). If anyone knows if this is possible to change back, please enlighten me ;-)

Thanks everybody who commented on this.

---

