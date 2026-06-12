---
title: "whats with all the play signs on internet videos?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mamamia88 on 2009-03-27
for some reason whenever i go to a page that has embedded video there is a big grey play sign over it is there something i can do to get rid of it?

---

### Post by Chemical Imbalance on 2009-03-27
that sounds like you have gnash installed instead of the adobe flash plugin.  gnash is an open-source alternative to flash.

Try looking in synaptic to see if you have gnash installed and remove it.  then download the non-free flash plugin.

---

### Post by mamamia88 on 2009-03-27
thats the thing i do have flash installed

---

### Post by Chemical Imbalance on 2009-03-27
did you check for gnash?

---

### Post by mamamia88 on 2009-03-27
yeah and it was unchecked

---

### Post by Chemical Imbalance on 2009-03-27
Can you post a screenshot?

---

### Post by mamamia88 on 2009-03-27
sure heres an example

---

### Post by Chemical Imbalance on 2009-03-27
> **mamamia88 said:**
> sure heres an example

That's definitely the Gnash thing I was talking about.

Try the search button in Synaptic for gnash.

Make sure *none* of the six or so results it outputs are installed--especially the mozilla plugin.

Also try searching for flash, then press the "S" button to organize the installed items first.  Make sure only the real flash is installed and no unnecessary plugins are check marked.

---

### Post by mamamia88 on 2009-03-27
there was nothing installed under gnash and swfdec-mozilla and libswfdec installed under flash can one of those be the cause?

---

### Post by Chemical Imbalance on 2009-03-28
> **mamamia88 said:**
> there was nothing installed under gnash and swfdec-mozilla and libswfdec installed under flash can one of those be the cause?

yes, that is the problem.  That is also an alternative flash plugin.

Remove both of those, then install ubuntu-restricted-extras

This will install codecs for your mediaplayers along with the proper Flash plugin from Adobe.

---

### Post by mamamia88 on 2009-03-28
cool it seems to be gone thanks

---

### Post by Chemical Imbalance on 2009-03-28
no problem

---

