---
title: "error message in LibreBase"
date: 2017-10-29
forum: Installation &amp; Upgrades
---

### Post by jduns on 2017-10-29
After upgrading from kubuntu 17.04 to kubuntu 17.10, with a macro stored not in a file, but in LibreOffice, as I say here: [https://ask.libreoffice.org/en/question/136379/avoid-error-message-in-base-with-a-writer-macro/ ]("https://ask.libreoffice.org/en/question/136379/avoid-error-message-in-base-with-a-writer-macro/")only in LibreBase, not in LibreCalc (nor in LibreWriter) I get an error message: "BASIC runtime error. Property or method not found: supportsService".
This is the macro
sub vai_qui
    If NOT ThisComponent.supportsService ("com.sun.star.text.TextDocument") Then
        Exit Sub
    End If

    oBookmarks = ThisComponent.getBookmarks ()
    If NOT oBookmarks.hasByName ("here") Then
        Exit Sub
    End If


    ViewCursor = ThisComponent.CurrentController.getviewCursor ()
    Bookmark = ThisComponent.Bookmarks.getByName ("here") .Anchor
    ViewCursor.gotorange (Bookmark, False)

    ViewCursor = ThisComponent.CurrentController.getviewCursor ()
    Bookmark = ThisComponent.Bookmarks.getByName ("here") .Anchor
    ViewCursor.gotorange (Bookmark, False)
end sub

Other users of LO say that in non-ubuntu release of LO this problem there isn't. Can you help me?
Thank you

---

### Post by jduns on 2017-11-10
This bug is in LibreOffice 5.4 realease, not in 5.3 (all working correctly).

---

