
COMMAND_CONFIRM_REGEX
^ok.*

POSITION_REPORT_REGEX
^.*X:(?<X>-?\d+\.\d+) Y:(?<Y>-?\d+\.\d+) Z:(?<Z>-?\d+\.\d+) .*A:(?<A>-?\d+\.\d+).*

COMMAND_ERROR_REGEX
^error:.*

CONNECT_COMMAND
G21 ; Set millimeters mode
G90 ; Set absolute positioning mode

HOME_COMMAND
G28;

HOME_COMPLETE_REGEX
^ok.*

SET_GLOBAL_OFFSETS_COMMAND
G92 {X:X%.4f} {Y:Y%.4f} {Z:Z%.4f} {A:A%.4f} ; reset coordinates

GET_POSITION_COMMAND
M114 ; get position

MOVE_TO_COMMAND
{Acceleration:M204 S%.2f} 
G0 {X:X%.4f} {Y:Y%.4f} {Z:Z%.4f} {A:A%.4f} {FeedRate:F%.2f} ; move to target

MOVE_TO_COMPLETE_COMMAND
M400 ; Wait for moves to complete before returning


H1 S1 ACTUATE_BOOLEAN_COMMAND
{True:M42 I P44 S255}{False:M42 I P44 S0}

H1 S2 ACTUATE_BOOLEAN_COMMAND
{True:M42 I P79 S255}{False:M42 I P79 S0}

H1VAC ACTUATE_BOOLEAN_COMMAND
{True:M42 I P14 S255}{False:M42 I P14 S0}

H1VAC ACTUATE_READ_COMMAND
M105 T0 ; Read T0 Analog Value

H1VAC ACTUATE_READ_REGEX
^ok.*T:(?<Value>\d+.\d+).*

H1 UPER LIGHT ACTUATE_BOOLEAN_COMMAND
{True:M42 I P63 S10}{False:M42 I P63 S0}


LOWER LIGHT ACTUATE_BOOLEAN_COMMAND
{True:M42 I P62 S55}{False:M42 I P62 S0}