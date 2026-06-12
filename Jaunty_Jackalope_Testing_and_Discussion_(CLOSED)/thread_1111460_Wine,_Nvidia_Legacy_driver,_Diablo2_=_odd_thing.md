---
title: "Wine, Nvidia Legacy driver, Diablo2 = odd thing"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by 4Orbs on 2009-03-30
Running Xubuntu Jaunty beta, fully updated, fresh install on real partitions, ext4. Using the nvidia driver 96.43.10 provided by the Hardware Drivers Mgr (p.s. the driver installed correctly, but the progress bar gave no indication of activity until the final 3% came up). Everything was looking nice and working well. Then I installed wine and installed Diablo2 game. This worked correctly, full screen was good as game loaded, pre-game cinema played, game menu worked, character selection worked. But when the actual game playing field started, the display was pushed halfway down the screen, and there was a ghost of the cursor from the previous screen glued to the display. So I changed game resolution to my not-preferred resolution, and the play field centered properly, but the cursor ghost remained.

I was hoping today's Wine update might correct the problem. It did not. So I deactivated the nvidia driver, then manually installed the latest 96.43.11 driver. This new driver did not fix anything, and appears to work equally to the previous.

My questions: Is this a driver quirk, a Wine problem, or an Xfce surprise? Should I expect future updates to fix this?

Thanks.

---

