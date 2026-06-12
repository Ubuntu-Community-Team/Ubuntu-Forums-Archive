---
title: "LAMP, JavaScript and character sets"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by HolidayQueen on 2010-04-17
Here's an oddity i have yet to figure out.

When PHP was serving up an article, it display all the french special chars properly.

When i wrote a javascript to fetch the article from the php script, and display it, the french special chars were screwed up.

adding meta-content tags to the html didn't fix it.
adding charset to the script tags didn't fix it.

What finally fixed it, was going into apache's config and uncomment Adddefaultcharset and setting it to ISO-8859-1.

What i dont get is why the characters are displayed properly in every other circumstance, except when going through javascript.

Any thoughts? I don't even know if my solution is the "right" way, but for the moment, it's the only way i can get it to display the characters properly regardless of which scripting language is serving it up.

---

