---
title: "declaration issue...."
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by teja483 on 2011-06-13
CmdList Commands[NO_OF_COMMANDS] = { 
                        {"WM8", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WM16", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WM32", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM8", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM16", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM32", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RR", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WR", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"MR", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"MW", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RMW",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"CMP",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"PAUSE",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"SLEEP",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"MENU",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RUN",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WM32M",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM32M",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RRM",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"HELP",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                };





the above declaration is done in a C file.

when i compiled it i got this errors.

cc1: warnings being treated as errors
../../../../infra/tools/genie/src/cmdparser.c:5: warning: missing braces around initializer
../../../../infra/tools/genie/src/cmdparser.c:5: warning: (near initialization for ‘Commands[0].param[0]’)

where am i doing the mistake??????????????????/:(

---

### Post by StrayEddy on 2011-06-13
Shouln't it be:

> **teja483 said:**
> CmdList Commands[NO_OF_COMMANDS] = { 
                        {"WM8", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WM16", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WM32", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM8", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM16", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM32", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RR", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WR", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"MR", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"MW", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RMW",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"CMP",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"PAUSE",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"SLEEP",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"MENU",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RUN",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WM32M",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM32M",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RRM",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"HELP",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL**}}};**


---

### Post by teja483 on 2011-06-13
yeah i have declared like that only whats the mistake in ti?

---

### Post by teja483 on 2011-06-13
CmdList Commands[NO_OF_COMMANDS] = {        {"WM8", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WM16", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WM32", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM8", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM16", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM32", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RR", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WR", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"MR", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"MW", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RMW",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"CMP",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"PAUSE",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"SLEEP",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"MENU",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RUN",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WM32M",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM32M",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RRM",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"HELP",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}}; 


i have done as you said it but no use......

cc1: warnings being treated as errors
../../../../infra/tools/genie/src/cmdparser.c:4: warning: missing braces around initializer
../../../../infra/tools/genie/src/cmdparser.c:4: warning: (near initialization for ‘Commands[0].param[0]’)

---

### Post by teja483 on 2011-06-13
its declared like this in the header file.....

extern CmdList Commands[NO_OF_COMMANDS];



please replyyyyyyyyyyyyyyyyyyyy:confused:



plzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz

---

### Post by teja483 on 2011-06-13
{
#define NO_OF_COMMANDS       20

typedef struct cmdlist {
                char cmd[15]; 
                char param[USR_CMD_MAX_NO_OF_PARAMS][50];
            }CmdList;


extern CmdList Commands[NO_OF_COMMANDS];
}

this is declared in the header file.....
 and in the C file    it is used as


CmdList Commands[NO_OF_COMMANDS] = {        {"WM8", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WM16", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WM32", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM8", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM16", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM32", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RR", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WR", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"MR", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"MW", {(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RMW",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"CMP",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"PAUSE",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"SLEEP",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"MENU",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RUN",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"WM32M",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RM32M",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"RRM",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}, 
                        {"HELP",{(char)NULL, (char)NULL, (char)NULL, (char)NULL, (char)NULL}}
                };



cc1: warnings being treated as errors
../../../../infra/tools/genie/src/cmdparser.c:4: warning: missing braces around initializer
../../../../infra/tools/genie/src/cmdparser.c:4: warning: (near initialization for ‘Commands[0].param[0]’)


what is the remedy for this



plzzzzzz help

time is runnig out......

---

### Post by teja483 on 2011-06-13
i dont know this is the correct answer or not .

but i evaded that problem with this

i declared        extern struct  CmdList Commands[NO_OF_COMMANDS];

instead of         extern  CmdList Commands[NO_OF_COMMANDS];

in the cmdparser.h   header file.

---

