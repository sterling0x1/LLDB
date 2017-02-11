# LLDB
A collection of LLDB aliases/regexes and Python scripts to aid in your debugging sessions

## Installation 

  1. Download scripts. Install to a dir of your choosing (i.e. `~/lldb`)
  2. In `~/.lldbinit` add the following:
      `command script import path/to/lldb_file.py`
  
  You must import each file individually in your lldbinit file


### find
  Finds all subclasses of a class. This class must by dynamic (aka inherit from a NSObject class). Currently doesn't work with   NSString or NSNumber (tagged pointer objects). 
  
  Example: 
  
      # Find all instances and subclasses of UIView
      (lldb)  find UIView
      
      # Find all instances of UIView that are UIViews. Ignore subclasses.
      (lldb) find UIView -e
      
      #Find all instances of UIView whose tag is equal to 5. Objective-C syntax only. Can reference object by 'obj'
      (lldb) find UIView -c "[obj tag]==5"

### yoink

  Takes a path on a iOS/tvOS/watchOS and writes to the **/tmp/** dir on your computer.
  If it can be read by `-[NSData dataWithContentsOfFile:]`, it can be written to disk

  Example (on iOS 10 device): 
  
      (lldb) yoink /System/Library/Messages/iMessageEffects/CKConfettiEffect.bundle/CKConfettiEffect

![yoink example](https://github.com/DerekSelander/LLDB/raw/master/Media/yoink_gif.gif)
