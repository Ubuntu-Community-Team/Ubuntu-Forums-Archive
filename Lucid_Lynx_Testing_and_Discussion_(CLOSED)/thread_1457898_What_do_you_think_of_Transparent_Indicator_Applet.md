---
title: "What do you think of Transparent Indicator Applet?"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-19
and an option to do application places and system panel also transparent?

i made my top and bottom panel slightly transparent as you can see in the attached 

picture my only problem in the top panel Indicator Applet and application places and 

and system applets so is there there something that i can do about it or you could add to 

the final lucid?

thanks in advance.

---

### Post by Atermoon on 2010-04-19
> **aviramof said:**
> s there there something that i can do about it or you could add to 

the final lucid?

thanks in advance.

Change your theme or if you really want to use the one you currently have edit the gtkrc to remove the pixmap bg from the panel.

---

### Post by bpickel on 2010-04-19
If you are able to run desktop effects, download the Compiz settings manager.

sudo apt-get install compizconfig-settings-manager

Once you have that installed, Go to 

System > Preferences > CompizConfig Settings Manager 

 Once you have the manager launched, look for the Opacity Brightness and Saturation plugin under Accessibility. Click on it to launch the settings for the plugin. 

 When you are in the plugin settings page first enable the plugin by placing a check in the box under Use This Plugin on the left of the screen. If it is already checked then ignore this step. 

 You should start on the Opacity tab and that is where we want to be. About mid screen you will see a section called Window specific settings. This is where we can tell Compiz to control the opacity of your Gnome Panels. This will affect the panel and everything on it, including the indicator applets. 


 If Windows specific settings is not expanded do so by clicking the plus. Once expanded you will see a button to add a new setting. 


 Click the New button. This will bring up an edit window where we can add this setting. A word of caution here. Always move the slider which will default to 0 to a higher setting, say above 50%. This reason for this is that if you add an visual element with the slider set to 0 it will have no Opacity and therefore you wouldn't be able to see. This can be problematic when certain elements disappear. 


 Ok, now to add your panels. Click the green plus beside the text box that is labeled Windows. This will open another edit screen. There will be an drop down box that will be defaulted to Window Class. That is what we want so leave it alone. Directly below that there is a text box labeled Value. This is where we tell Compiz what we want to affect. Click on the Grab button. Your pointer will turn into a + mark. Be careful at this point because whatever you click on will have its text value added to the Value box.  When you have the + pointer, click on one of your panels. This should add something like Gnome-panel in the Value field. Click add. This should take you back to the original edit box. The field labeled Windows should now read class=Gnome-panel.  

  I have seen the grab not work properly and you may see only class=. If this happens all of your windows will be effected. That is why we moved the slider over from 0 earlier. If you end up here simply type Gnome-panel to make the string read: 

class=Gnome-panel


 Now adjust the slider to make the panels as Opaque as you like. If this does not work then change the string class=Gnome-panel to class=gnome-panel. 

 Sometimes the panel will be registered as this and Ubuntu being a *nix box, case does matter.   I included all the the steps above as the grab usually gets the right string. Sorry if you already know how to this. I just wanted to type it out if anyone else was interested.

---

### Post by aviramof on 2010-04-19
i use SphereCrystal do you know something better that would show Indicator Applet as transparent

it seem to be that the panel properties have no influence on this indicators.

---

### Post by Atermoon on 2010-04-19
> **aviramof said:**
> i use SphereCrystal do you know something better that would show Indicator Applet as transparent

it seem to be that the panel properties have no influence on this indicators.

The indicators have nothing to do with this, it's a theme setting. Try clearlooks for example and you'll see the difference.

---

### Post by aviramof on 2010-04-19
I see now it looks better except that i don't like the color of folders and etc i prefer blue color i would create a costume theme which is the mix of this two themes.

thanks for the information and for the help.:)

---

### Post by Atermoon on 2010-04-19
> **aviramof said:**
> I see now it looks better except that i don't like the color of folders and etc i prefer blue color i would create a costume theme which is the mix of this two themes.

thanks for the information and for the help.:)

Just change the icon theme then :)

---

### Post by MarkieB on 2010-04-19
no longer participating in ubuntuforums.org

---

### Post by aviramof on 2010-04-19
thanks for the information maybe i would check it soon with my SphereCrystal theme.:)

it's very strange but i can't find  bg_pixmap in /usr/share/themes/SphereCrystal/gtk-2.0/gtkrc just a lot of pixmap i can't even find panel.

```
# SphereCrystal gtk theme
# (c) 2002-2003  Christian Schaller <Uraeus@gnome.org>
# (c) 2002-2003  oprime <http://themes.freshmeat.net/~oprime/>
# (c) 2002-2003 Andrew Duhan <andrew@duhan.net>

style "base"
{
   fg[NORMAL]      = "#000000" 
  fg[PRELIGHT]    = "#000000" 
  fg[ACTIVE]      = "#000000" 
  fg[SELECTED]    = "#000000" 
  fg[INSENSITIVE] = "#999999" 
  bg[NORMAL]      = "#f6f6f6" 
  bg[PRELIGHT]    = "#cccccc"
  bg[ACTIVE]      = "#cccccc"
  bg[SELECTED]    = "#a6b5bf"
  bg[INSENSITIVE] = "#cccccc"
  base[NORMAL]    = "#ffffff"
  base[SELECTED]  = "#a6b5bf"
  base[ACTIVE]    = "#a6b5bf"
  GtkRange::slider_width = 15
  GtkScrollbar::min_slider_length = 15
  # Sets the color of the cursor  
  GtkEntry::cursor_color = "#000000" 
  GtkTextView::cursor_color = "#000000"
} class "*" style "base"

style "default"
{
  engine "pixmap" 
    {
  image {
            function        = SLIDER
            recolorable     = TRUE
            file            = "scrollbar_horizontal.svg"
            border          = { 10, 10, 6, 7 }
            stretch         = TRUE
            orientation     = HORIZONTAL
        }
        image {
            function        = SLIDER
            recolorable     = TRUE
            file            = "scrollbar_vertical.svg"
            border          = { 6, 7, 10, 10 }
            stretch         = TRUE
            orientation     = VERTICAL
        }
  
  image {
            function        = BOX
            recolorable     = TRUE
            detail          = "slider"
            state           = PRELIGHT
            file            = "scrollbar_prelight_horizontal.svg"
            border          = { 10, 10, 6, 7 }
            stretch         = TRUE
            orientation     = HORIZONTAL
        }
        image {
            function        = BOX
            recolorable     = TRUE
            detail          = "slider"
            file            = "scrollbar_horizontal.svg"
            border          = { 10, 10, 6, 7 }
            stretch         = TRUE
            orientation     = HORIZONTAL
        }
        image {
            function        = BOX
            recolorable     = TRUE
            detail          = "slider"
            state           = PRELIGHT
            file            = "scrollbar_prelight_vertical.svg"
            border          = { 6, 7, 10, 10 }
            stretch         = TRUE
            orientation     = VERTICAL
        }
        image {
            function        = BOX
            recolorable     = TRUE
            detail          = "slider"
            file            = "scrollbar_vertical.svg"
            border          = { 6, 7, 10, 10 }
            stretch         = TRUE
            orientation     = VERTICAL
        } 
    image {
            function        = BOX
            recolorable     = TRUE
            detail          = "paned"
            file            = "paned.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }

    image {
            function        = BOX
            recolorable     = TRUE
            detail          = "trough"
            file            = "vertical_trough.png"
            border          = { 2, 2, 1, 1 }
            stretch         = TRUE
            orientation     = VERTICAL
        }
    # This entry sets the background image used for the menubar
    image {
            function        = BOX
            recolorable     = TRUE
            detail          = "menubar"
            file            = "menubar_background.png"
            border          = { 2, 2, 1, 1 }
            stretch         = TRUE
            orientation     = VERTICAL
        }

        image {
            function        = BOX
            recolorable     = TRUE
            detail          = "trough"
            file            = "horizontal_trough.png"
            border          = { 1, 1, 2, 2 }
            stretch         = TRUE
            orientation     = HORIZONTAL
        }
image { 
            function        = FLAT_BOX
            recolorable     = TRUE
            detail          = "tooltip"
            file            = "tooltip.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
image {
            function        = BOX
            recolorable     = TRUE
            detail          = "handlebox_bin"
            file            = "handlebox.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
image {
            function        = FLAT_BOX
            recolorable     = TRUE
            state           = INSENSITIVE
            detail          = "selected"
            file            = "text_selected_insensitive.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = FLAT_BOX
            recolorable     = TRUE
            detail          = "selected"
            file            = "text_selected.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = FLAT_BOX
            recolorable     = TRUE
            state           = INSENSITIVE
            detail          = "text"
            file            = "text_insensitive.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = FLAT_BOX
            recolorable     = TRUE
            detail          = "text"
            file            = "text_selected.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = FLAT_BOX
            recolorable     = TRUE
            detail          = "viewportbin"
            file            = "background.png"
            stretch         = FALSE
        }
####################
    
    image {
            function        = BOX
            recolorable     = TRUE
            shadow          = IN
            file            = "extraA_box.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = BOX
            recolorable     = TRUE
            file            = "extraB_box.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
 image {
            function        = OPTION
            recolorable     = TRUE
            shadow          = OUT
            overlay_file    = "option_out.png"
            overlay_border  = { 0, 0, 0, 0 }
            overlay_stretch = FALSE
        }
        image {
            function        = OPTION
            recolorable     = TRUE
            shadow          = IN
            overlay_file    = "option_in.png"
            overlay_border  = { 0, 0, 0, 0 }
            overlay_stretch = FALSE
        }

image {
            function        = CHECK
            recolorable     = TRUE
            shadow          = OUT
            overlay_file    = "check_out.png" 
            overlay_stretch = FALSE
        }
        image {
            function        = CHECK
            recolorable     = TRUE
            shadow          = IN
            overlay_file    = "check_in.png" 
            overlay_stretch = FALSE
        }
    
  image {
            function        = HANDLE
            recolorable     = TRUE
            file            = "handle_bar.png"
            border          = { 10, 5, 5, 10 }
            stretch         = TRUE
            overlay_file    = "handle_vert_thumb.png"
            overlay_border  = { 0, 0, 0, 0 }
            overlay_stretch = FALSE
            orientation     = VERTICAL
        }
    image 
      {
        function        = FOCUS
    recolorable     = TRUE
    overlay_file    = "blank.png"
    overlay_border  = { 0,0,0,0 }
    overlay_stretch = TRUE
      }

### These are the arrows used in scrollbar handles, drop-down menu's etc.
   image
     {
        function        = ARROW
    recolorable     = TRUE
    state           = NORMAL
    file            = "arrow_up_normal.svg"
    stretch         = TRUE
    arrow_direction = UP
      }
       
    image 
      {
        function        = ARROW
    recolorable     = TRUE
    state           = PRELIGHT
    file            = "arrow_up_normal.svg"
    stretch         = TRUE
    arrow_direction = UP
      }
    image 
      {
        function        = ARROW
    recolorable     = TRUE
        shadow          = IN
    file            = "arrow_up_clicked.svg"
    stretch         = TRUE
    arrow_direction = UP
      }
    image 
      {
        function        = ARROW
    recolorable     = TRUE
    state           = INSENSITIVE
    file            = "arrow_up_normal.svg"
    stretch         = TRUE
    arrow_direction = UP
      }

    image 
      {
        function        = ARROW
    recolorable     = TRUE
    state           = NORMAL
    file            = "arrow_down_normal.svg"
    stretch         = TRUE
    arrow_direction = DOWN
      }
    image 
      {
        function        = ARROW
    recolorable     = TRUE
    state           = PRELIGHT
    file            = "arrow_down_normal.svg"
    stretch         = TRUE
    arrow_direction = DOWN
      }
    image 
      {
        function        = ARROW
    recolorable     = TRUE
        shadow          = IN
    file            = "arrow_down_clicked.svg"
    stretch         = TRUE
    arrow_direction = DOWN
      }
    image 
      {
        function        = ARROW
    recolorable     = TRUE
    state        = INSENSITIVE
    file            = "arrow_down_normal.svg"
    stretch         = TRUE
    arrow_direction = DOWN
      }

    image 
      {
        function        = ARROW
    recolorable     = TRUE
    state           = NORMAL
    file            = "arrow_left_normal.svg"
    stretch         = TRUE
    arrow_direction = LEFT
      }
    image 
      {
        function        = ARROW
    recolorable     = TRUE
    state           = PRELIGHT
    file            = "arrow_left_normal.svg"
    stretch         = TRUE
    arrow_direction = LEFT
      }
    image 
      {
        function        = ARROW
    recolorable     = TRUE
        shadow          = IN
    file            = "arrow_left_clicked.svg"
    stretch         = TRUE
    arrow_direction = LEFT
      }
    image 
      {
        function        = ARROW
    recolorable     = TRUE
    state           = INSENSITIVE
    file            = "arrow_left_normal.svg"
    stretch         = TRUE
    arrow_direction = LEFT
      }

    image 
      {
        function        = ARROW
    recolorable     = TRUE
    state           = NORMAL
    file            = "arrow_right_normal.svg"
    stretch         = TRUE
    arrow_direction = RIGHT
      }
    image 
      {
        function        = ARROW
    recolorable     = TRUE
    state           = PRELIGHT
    file            = "arrow_right_normal.svg"
    stretch         = TRUE
    arrow_direction = RIGHT
      }
    image 
      {
        function        = ARROW
    recolorable     = TRUE
        shadow          = IN
    file            = "arrow_right_clicked.svg"
    stretch         = TRUE
    arrow_direction = RIGHT
      }
    image {
            function        = HLINE
            recolorable     = TRUE
            file            = "horizontal_line.png"
            border          = { 0, 0, 1, 1 }
            stretch         = TRUE
        }
        image {
            function        = VLINE
            recolorable     = TRUE
            file            = "vertical_line.png"
            border          = { 1, 1, 0, 0 }
            stretch         = TRUE
        }
image {
            function        = FLAT_BOX
            recolorable     = TRUE
            state           = INSENSITIVE
            detail          = "entry_bg"
            file            = "entry_bg.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = FLAT_BOX
            recolorable     = TRUE
            detail          = "entry_bg"
            file            = "entry_bg.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
    image 
      {
        function        = ARROW
    recolorable     = TRUE
    state           = INSENSITIVE
    file            = "arrow_right_normal.svg"
    stretch         = TRUE
    arrow_direction = RIGHT
      }
    image {
            function        = SHADOW
            recolorable     = TRUE
            shadow          = IN
            file            = "shadow_in.png"
            border          = { 1, 1, 1, 1 }
            stretch         = TRUE
        }
        image {
            function        = SHADOW
            recolorable     = TRUE
            shadow          = OUT
            file            = "shadow_out.png"
            border          = { 1, 1, 1, 1 }
            stretch         = TRUE
        }
        image {
            function        = SHADOW
            recolorable     = TRUE
            shadow          = ETCHED_IN
            file            = "etched.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = SHADOW
            recolorable     = TRUE
            shadow          = ETCHED_OUT
            file            = "etched.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
   }
}



# common default
widget_class "*" style "default"
# Many themes engines use class "GtkWidget" style "default"
# instead. This is broken.

style "window" 
{
  engine "pixmap" {
    image 
      {
    function        = FLAT_BOX
    recolorable     = TRUE
    file            = "background.png"
    stretch         = FALSE
      }
  }
}

class "GtkWindow" style "window"

###########################################
# Buttons
###########################################
#

style "CheckRadioButton" {
    engine "pixmap" {
        image {
            function        = FLAT_BOX
            recolorable     = TRUE
            file            = "menu_hi-light.png"
            border          = { 10, 10, 10, 10 }
            stretch         = TRUE
        }
    }
}

class "*RadioButton*" style "CheckRadioButton"
class "*CheckButton*" style "CheckRadioButton"

#
###########################################

###########################################
#

 style "ToggleButton" {
    engine "pixmap" {
        image {
            function        = BOX
            recolorable     = TRUE
            shadow          = IN
            file            = "toggle_clicked.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = BOX
            recolorable     = TRUE
            shadow          = OUT
            file            = "toggle_default.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
    }
 }
class "*ToggleButton*" style "ToggleButton"

#
###########################################

###########################################
#

style "Button" {
    bg[NORMAL] = "#ffffff"
    
    engine "pixmap" {
        image {
            function        = BOX
            recolorable     = TRUE
            state           = NORMAL
            detail          = "buttondefault"
            shadow          = IN 
            file            = "clear.png"
            border          = { 0, 0, 0, 0 }
            stretch         = FALSE 
        }
        image {
            function        = BOX
            recolorable     = TRUE
            state           = NORMAL
            shadow          = IN 
            file            = "button_normal_in.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = BOX
            recolorable     = TRUE
            state           = NORMAL
            shadow          = OUT
            file            = "button_normal_out.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = BOX
            recolorable     = TRUE
            state           = INSENSITIVE 
            shadow          = IN
            file            = "button_insensitive_in.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = BOX
            recolorable     = TRUE
            state           = INSENSITIVE
            shadow          = OUT
            file            = "button_insensitive_out.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = BOX
            recolorable     = TRUE
            state           = PRELIGHT 
            shadow          = OUT
            file            = "button_prelight_out.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = BOX
            recolorable     = TRUE
            state           = SELECTED 
            shadow          = IN
            file            = "button_selected_in.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = BOX
            recolorable     = TRUE
            state           = ACTIVE 
            shadow          = IN
            file            = "button_active_in.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
    }
}
class "*Button*" style "Button"

#
###########################################

###########################################
# Notebooks
###########################################
#

style "Notebook" {

    engine "pixmap" {
        image {
            function        = EXTENSION
            recolorable     = TRUE
            state           = ACTIVE
            file            = "notebook_active_bottom.png"
            border          = { 10, 10, 10, 10 }
            stretch         = TRUE
            gap_side        = BOTTOM
        }
        image {
            function        = EXTENSION
            recolorable     = TRUE
            state           = ACTIVE
            file            = "notebook_active_top.png"
            border          = { 10, 10, 10, 10 }
            stretch         = TRUE
            gap_side        = TOP
        }

        image {
            function        = EXTENSION
            recolorable     = TRUE
            state           = ACTIVE
            file            = "extension_active_right.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
            gap_side        = RIGHT
        }
        image {
             function        = EXTENSION
             recolorable     = TRUE
             state           = ACTIVE
             file            = "extension_active_left.png"
             border          = { 2, 2, 2, 2 }
             stretch         = TRUE
             gap_side        = LEFT
        }

        image {
            function        = EXTENSION
            recolorable     = TRUE
            file            = "notebook_bottom.png"
            border          = { 10, 10, 10, 10 }
            stretch         = TRUE
            gap_side        = BOTTOM
        }
        image {
            function        = EXTENSION
            recolorable     = TRUE
            file            = "notebook_top.png"
            border          = { 10, 10, 10, 10 }
            stretch         = TRUE
            gap_side        = TOP
        }
        image {
            function        = EXTENSION
            recolorable     = TRUE
            file            = "extension_right.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
            gap_side        = RIGHT
        }
        image {
            function        = EXTENSION
            recolorable     = TRUE
            file            = "extension_left.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
            gap_side        = LEFT
        }
        
        ############################################
        # How to draw boxes with a gap on on side
        # (ie the page of a notebook)
        ############################################

        image {
            function        = BOX_GAP
            recolorable     = TRUE
            file            = "box_gap_top.png"
            border          = { 1, 1, 2, 1 }
            stretch         = TRUE 
            gap_file        = "box_gap_top_focus.png"
            gap_border      = { 1, 1, 0, 0 }
            gap_start_file  = "box_gap_top_start.png"
            gap_start_border= { 0, 0, 0, 1 }
            gap_end_file    = "box_gap_top_end.png"
            gap_end_border  = { 0, 0, 0, 1 }
            gap_side        = TOP
        }
        image {
            function        = BOX_GAP
            recolorable     = TRUE
            file            = "box_gap_bottom.png"
            border          = { 1, 1, 1, 2 }
            stretch         = TRUE
            gap_file        = "box_gap_bottom_focus.png"
            gap_border      = { 1, 1, 0, 0 }
            gap_start_file  = "box_gap_bottom_start.png"
            gap_start_border= { 0, 0, 1, 0 }
            gap_end_file    = "box_gap_bottom_end.png"
            gap_end_border  = { 0, 0, 1, 0 }
            gap_side        = BOTTOM
        }
        image {
            function        = BOX_GAP
            recolorable     = TRUE
            file            = "box_gap_left.png"
            border          = { 2, 1, 1, 1 }
            stretch         = TRUE
            gap_file        = "box_gap_left_focus.png"
            gap_border      = { 0, 0, 1, 1 }
            gap_start_file  = "box_gap_left_start.png"
            gap_start_border= { 0, 1, 0, 0 }
            gap_end_file    = "box_gap_left_end.png"
            gap_end_border  = { 0, 1, 0, 0 }
            gap_side        = LEFT
        }
        image {
            function        = BOX_GAP
            recolorable     = TRUE
            file            = "box_gap_right.png"
            border          = { 1, 2, 1, 1 }
            stretch         = TRUE
            gap_file        = "box_gap_right_focus.png"
            gap_border      = { 0, 0, 1, 1 }
            gap_start_file  = "box_gap_right_start.png"
            gap_start_border= { 1, 0, 0, 0 }
            gap_end_file    = "box_gap_right_end.png"
            gap_end_border  = { 1, 0, 0, 0 }
            gap_side        = RIGHT
        }

        ############################################
        # How to draw the box of a notebook when it 
        # is not attached to a tab
        ############################################

        image {
            function        = BOX
            recolorable     = TRUE
            file            = "notebook_unattached.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
            gap_side        = TOP
        }
    }
}

class "*Notebook*" style "Notebook"

#
###########################################

###########################################
#

 style "MenuItem" {
    engine "pixmap" {
        image {
            function        = BOX
            recolorable     = TRUE
            file            = "menu_hi-light.png"
            border          = { 10, 10, 10, 10 }
            stretch         = TRUE
        }
    }
}

class "*MenuItem*" style "MenuItem"

#
###########################################

###########################################
#

 style "OptionMenu" {
    #This pixmap will be used to represent the body of the 
    #option menu(much like a combo box, but a menu drop 
    #down with various options from which to choose).
    #it is important to note(as stated below) that this should not
    #include the handle portion of the box, which is often two arrows
    #or a box.
    engine "pixmap" {
      #in the pixmap engine each theme part is represented by
      #a subsection  representing how and where that pixmap 
      #should be used, and what file to use etc...
        image {
         #the funtion variable defines what this image
         #will be used for, which part of an object,
         #the valid values are as follows:
         #HLINE, VLINE, SHADOW, POLYGON, ARROW, DIAMOND,        
         #OVAL, STRING, BOX, FLAT_BOX, CHECK, OPTION, CROSS,         
         #RAMP, TAB, SHADOW_GAP, BOX_GAP, EXTENSION, FOCUS,    
         #SLIDER, ENTRY, HANDLE, STEPPER
            function        = BOX
            recolorable     = TRUE
            file            = "menubar_option.png"
            border          = { 12, 18, 9, 10 }
            stretch         = TRUE
        }
    }
    #In gtk draw/paint tab is something of a misnomer,
    #as in reality what it draws is the arrows or box handle 
    #in a drop down option menu. Thus to prevent double drawing
    #of this so called TAB in a pixmap theme, the arrows, or whatever 
    #is chosen to rpresent this handle must be its own png or svg, and
    # should not be part of the BOX png.
  engine "pixmap" {
        image {
            function        = TAB
            recolorable     = TRUE
            file            = "blank.png"
            border          = { 12, 18, 9, 10 }
            stretch         = TRUE
        }
    }
}
class "*OptionMenu*" style "OptionMenu"
widget_class "*OptionMenu*" style "OptionMenu"

#
###########################################

###########################################
#

style "ProgressBar" {
    engine "pixmap" {
        image {
            function        = BOX
            recolorable     = TRUE
            detail          = "bar"
            file            = "progressbar.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image {
            function        = BOX
            recolorable     = TRUE
            detail          = "trough"
            file            = "trough.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
            orientation     = HORIZONTAL
        }
    }
}

class "*ProgressBar*" style "ProgressBar"
widget_class "*ProgressBar*" style "ProgressBar"

#
###########################################

###########################################
#

style "Ruler" {     
    engine "pixmap" {
        image {
            function        = BOX
            recolorable     = TRUE
            detail          = "vruler"
            file            = "vertical_ruler.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image { 
            function        = BOX
            recolorable     = TRUE
            detail          = "hruler"
            file            = "horzontal_ruler.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
    }   
}
class "*Ruler*" style "Ruler"

#
###########################################

###########################################
#

 style "Item" {     
    engine "pixmap" {
        image {
            function        = FLAT_BOX
            recolorable     = TRUE
            state           = INSENSITIVE
            file            = "item_insensitive.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
        image { 
            function        = FLAT_BOX
            recolorable     = TRUE
            file            = "item.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
    } 
}
class "*TreeItem*" style "Item"
class "*ListItem*" style "Item"

#
###########################################

###########################################
#

style "Window" {   
    engine "pixmap" {
        image {
            function        = FLAT_BOX
            recolorable     = TRUE
            file            = "window_background.png"
            stretch         = FALSE
        }
    }
}

class "*Window*" style "Window"

#
###########################################

###########################################
#

 style "Curve" {
    engine "pixmap" { 
        image {
            function        = FLAT_BOX
            recolorable     = TRUE
            detail          = "curve_bg"
            file            = "curve_background.png"
            border          = { 2, 2, 2, 2 }
            stretch         = TRUE
        }
    } 
}     
  
class "*Curve*" style "Curve"
```

---

### Post by MarkieB on 2010-04-20
no longer participating in ubuntuforums.org

---

### Post by d3v1150m471c on 2010-04-20
Try using something like that as your panel. Right click the panel and set it to use that as an image. Also, adjust your controls in your theme. This is probably why your indicator applet is not just icons on the panel.

---

