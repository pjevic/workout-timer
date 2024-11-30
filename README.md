<!-- @format -->

# Workout Timer

## **`React.memo`**

`React.memo` is a higher-order component that memoizes the result of a component’s render. It prevents re-renders unless the props change, optimizing performance for functional components.

### **Usage in the App**

1. **`Calculator` Component**
   ```javascript
   export default memo(Calculator);
   ```
2. **`ToggleSounds` Component**

   ```jsx
   export default memo(ToggleSounds);
   ```

   - Prevents unnecessary updates when toggling sound.
   - ToggleSounds is lightweight, but memoization avoids unnecessary DOM updates.

---

## **`useMemo`**

`useMemo` caches the result of an expensive calculation and recomputes it only when its dependencies change.

### **Usage in the App**

1. **Memoizing the `workouts` Array**
   ```jsx
   const workouts = useMemo(
     () => [
       { name: "Full-body workout", numExercises: partOfDay === "AM" ? 9 : 8 },
       { name: "Arms + Legs", numExercises: 6 },
       { name: "Arms only", numExercises: 3 },
       { name: "Legs only", numExercises: 4 },
       { name: "Core only", numExercises: partOfDay === "AM" ? 5 : 4 },
     ],
     [partOfDay]
   );
   ```
   - Ensures the workouts array is recalculated only when the partOfDay (AM/PM) changes.
   - Avoids unnecessary recalculations on every render, improving efficiency.

## **Performance Summary**

| Component      | Optimization Method | Purpose                                                      |
| -------------- | ------------------- | ------------------------------------------------------------ |
| `Calculator`   | `React.memo`        | Prevent re-renders unless `workouts` or `allowSound` change. |
| `ToggleSounds` | `React.memo`        | Avoid re-renders when sound state toggles.                   |
| `workouts`     | `useMemo`           | Cache the workouts array based on `partOfDay`.               |
