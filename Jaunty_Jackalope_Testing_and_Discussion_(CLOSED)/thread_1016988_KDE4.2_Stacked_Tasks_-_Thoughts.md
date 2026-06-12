---
title: "KDE4.2 Stacked Tasks - Thoughts?"
date: 2008-12-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tripinva on 2008-12-20
Hello:

To anyone using stacked tasks in the latest KDE 4.2 Beta, are you finding that the stack ordering is very annoying and counter intuitive?  Instead of stacking:

KDE3 Method
1  4  7
2  5  8
3  6  9

It stacks:

KDE4.2 Beta Method
1  2  3
4  5  6
7  8  9

Which is annoying because when something new opens, everything gets moved around.  Compare:

KDE3 Method
1  4  7  10
2  5  8
3  6  9

KDE4.2 Method
1  2  3  4
5  6  7  8
9  10

See the concern?  There was a bug report that was already filed that I commented on and voted for here:

[https://bugs.kde.org/show_bug.cgi?id=177687](https://bugs.kde.org/show_bug.cgi?id=177687)

Anyone else have any thoughts on this?

- Trip

---

### Post by vishalrao on 2008-12-20
i'd prefer the KDE 4.2 method without the rearranging, being a left-to-right and top-to-bottom (english) reader :D

so the fix should be:

KDE4.2:

1  2  3

4  5  6

7  8  9

10

---

