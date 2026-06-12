---
title: "Special keys don't work after last updates"
date: 2008-09-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by roberine on 2008-09-09
Clean install of Ibex A5, AMD64
After installing the the latest updates tonight the following keys no longer work: up-down-left-right-insert-home-end-delete-page up/down
(the keys left to the nummeric keypad)
Strangely they do still work on the numeric keypad on the right.
Any ideas how to solve this and what's responsible for this.
PS. The keys work on the login screen.

Thanks,
HerbY

---

### Post by jalmargyyk on 2008-09-09
I lost my keyboard layout and now it defaults back to US layout. I also can't change it from the System -> Settings -> Keyboard, because it (gnome-keyboard-properties) crashes after that. I wonder if these symptoms could be related with the ones you are experiencing?

---

### Post by tepsipakki on 2008-09-09
upgrade again, xkb-data probably didn't get updated.

---

### Post by pressureman on 2008-09-10
I'm seeing this problem too. If you bring up a keyboard layout on-screen, it appears that the arrow keys are being misinterpreted as follows:

left-arrow: right-alt
up-arrow: printscreen
down-arrow: right-superkey
right-arrow: (nothing)

in addition to that:
right-control: page-down
right-alt: numkey-enter
end: left-superkey
page-down: windows-context-menu
page-up: numkey-division
home: pause
insert: (nothing)
delete: (nothing)

It's pretty whacked.

---

### Post by roberine on 2008-09-10
After this mornings updates everythings back to normal.
So no more problems.

---

