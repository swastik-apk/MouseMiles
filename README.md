# Windows Mouse Metrics Tracker [MouseMiles]

## Overview

This application is a Windows desktop tool developed using C# and WPF (.NET) designed to capture, analyze, and visualize mouse interaction data which can be useful for usability studies, interface design improvements, performance analysis, or personal productivity tracking.

The application focuses on capturing fundamental mouse events directly within its own context or potentially globally (see Future Enhancements) using Windows mechanisms and .NET event handling.

## Features

This application aims to track and present the following mouse metrics:

*   **Distance Moved:**
    *   Calculates the cumulative distance the mouse cursor travels.
    *   Based on monitoring `MouseMove` events and calculating the Euclidean distance between consecutive points.
*   **Clicks:**
    *   Tracks the total number of mouse clicks.
    *   Identifies the type of button pressed (Left, Right, Middle, XButton1, XButton2).
    *   Records the screen coordinates (X, Y) of each click.
    *   Logs the timestamp for each click event.
    *   Distinguishes between single and double clicks (`ClickCount`).
*   **Scroll Wheel Usage:**
    *   Monitors the rotation of the mouse scroll wheel.
    *   Quantifies the amount of scrolling (`Delta`).
    *   Detects the direction of scrolling (forward/up or backward/down).
*   **(Planned/Optional) Hover Time:**
    *   Measure the duration the mouse cursor remains stationary over specific UI elements within the application.

## Technology Stack

*   **Language:** C#
*   **Framework:** WPF (Windows Presentation Foundation)
*   **Platform:** .NET ([Specify .NET Version, e.g., .NET 8.0, .NET Framework 4.8])
*   **IDE (Recommended):** Visual Studio 2022+
*   **Build Tool:** MSBuild (via Visual Studio or `dotnet build`)

## Prerequisites

*   Windows Operating System (Windows 10 or later recommended)
*   .NET SDK ([Specify matching .NET Version])
*   Visual Studio ([Specify Version, e.g., 2022]) with the ".NET desktop development" workload installed.

## Getting Started

1.  **Clone the repository:**
    ```bash
    git clone [URL of your repository]
    cd [repository folder]
    ```
2.  **Open the solution:**
    *   Open the `.sln` file in Visual Studio.
3.  **Build the solution:**
    *   Press `Ctrl+Shift+B` or go to `Build > Build Solution`.
4.  **Run the application:**
    *   Press `F5` or click the "Start" button in Visual Studio.
    *   Alternatively, navigate to the output directory (`bin\Debug\[net-version]\`) and run the `.exe` file directly.

## Usage

1.  **Start Tracking:** Launch the application. Tracking may start automatically, or you might need to click a "Start Tracking" button.
2.  **Interact:** Use your mouse normally. The application will capture events in the background (initially likely within its own window context, unless global hooks are implemented).
3.  **View Metrics:** The main application window will display the collected metrics in real-time or near real-time. This includes:
    *   Total distance moved (e.g., in pixels).
    *   Click counts per button type.
    *   Total scroll delta.
4.  **Stop Tracking:** Click a "Stop Tracking" button (if applicable).
5.  **Reset Metrics:** Use a "Reset" button to clear the current session's data and start fresh.
6.  **(Planned) Export Data:** Functionality to export the collected raw event data or summary metrics to formats like CSV or JSON for external analysis.

## Data Collected

The application captures the following data points from mouse events:

*   **MouseMove:** Timestamp, X coordinate, Y coordinate.
*   **MouseDown/MouseUp:** Timestamp, X coordinate, Y coordinate, Button type (Left, Right, Middle, XButton1, XButton2), Click count.
*   **MouseWheel:** Timestamp, X coordinate, Y coordinate, Scroll Delta.

*Note: Coordinates are typically relative to the application window or specific UI elements unless global hooks are used.*

## Visualization

The user interface provides:

*   **Real-time Displays:** Numerical counters and labels showing current metrics (distance, clicks, scroll).
*   **(Planned) Basic Charts:** Simple charts (e.g., bar charts for click distribution, line charts for distance over time) to visualize aggregated data.
*   **(Potential) Heatmaps:** Visual representation of cursor concentration areas (likely requires significant extra implementation).

## Potential Future Enhancements

*   **Global Mouse Hooking:** Implement system-wide mouse tracking (outside the application window) using libraries like `globalmousekeyhook` or direct P/Invoke calls to Windows APIs (`SetWindowsHookEx`).
*   **Advanced Visualization:** Implement heatmaps, path overlays, and more sophisticated charts using libraries like OxyPlot, LiveCharts, etc.
*   **Session Replay:** Record and playback sequences of mouse movements and clicks.
*   **Hover Tracking:** Implement reliable hover time detection over specific screen regions or application elements.
*   **Configuration:** Allow users to configure which metrics to track, sensitivity, data storage location, etc.
*   **Data Export/Import:** Robust options for exporting data in various formats (CSV, JSON, XML) and potentially importing previous sessions.
*   **Raw Input API:** Explore using the Raw Input API for high-precision, unfiltered mouse data, especially for tracking beyond screen boundaries.
*   **Privacy Features:** Add options for data anonymization or selective tracking.

## Privacy Considerations

This application tracks user mouse interactions.

*   **Transparency:** Be aware that this application records details about your mouse usage (movements, clicks, scrolling) including timestamps and coordinates.
*   **Data Storage:** Currently, data is likely stored in memory during runtime and potentially logged to a local file if export functionality is implemented. No data is transmitted externally unless explicitly designed to do so.
*   **Scope:** By default, tracking might be limited to the application's window. If global hooks are implemented, tracking will occur system-wide while the application is active. Use with caution.
*   **Distribution:** If distributing this application, clearly inform users about the data being collected and how it is used/stored. Ensure compliance with relevant privacy regulations.

## Contributing

[Add contribution guidelines here if you plan to accept contributions - e.g., how to report bugs, suggest features, or submit pull requests.]

## License

[Specify your chosen license here, e.g., MIT License. Include a LICENSE file in your repository.]

---
