---
tags:
  - appearance
  - font
---
# `bold_brightens_ansi_colors = true`

When true (the default), PaletteIndex 0-7 are shifted to bright when the font
intensity is bold.

This brightening effect doesn't occur when the text is set
to the default foreground color!

This defaults to true for better compatibility with a wide
range of mature software; for instance, a lot of software
assumes that Black+Bold renders as a Dark Grey which is
legible on a Black background, but if this option is set to
false, it would render as Black on Black.

{{since('20230320-124340-559cb7b0')}}

This option can now have one of three values:

* `"No"` - the bold attribute will not influence palette selection
* `"BrightAndBold"` - the bold attribute will select a bright version of palette indices 0-7 and preserve the bold attribute on the text, using both a bold font and a brighter color
* `"BrightOnly"` - the bold attribute will select a bright version of palette indices 0-7 but the intensity will be treated as normal and a non-bold font will be used for the text.

You may use `true` or `false` for backwards compatibility.  `true` is
equivalent to `"BrightAndBold"` and `false` is equivalent to `"No"`.

{{since('nightly')}}

Bold text in the default foreground color can be given its own color by
setting `bold = { fg = ... }` in the [colors](../../appearance.md#defining-your-own-colors)
section.  That color is used regardless of this option, but when this option
is set to `"BrightOnly"`, such text is also treated as normal intensity, so it
is drawn with a non-bold font in that color, the same as bright ansi colors:

```lua
config.bold_brightens_ansi_colors = 'BrightOnly'
config.colors = {
  bold = { fg = '#ffd866' },
}
```

